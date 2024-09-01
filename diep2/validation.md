---
id: validation
title: Validations
---

Form validation allows an error message to be displayed if the user has not correctly filled out the form with the expected type of input. It will either alert the user that they messed up and need to fix something to proceed, or the form will be validated and the user will be able to continue with their process. We have done validations at several levels which are explained below.

### Schema level validations

A schema is a set of rules that define how a data set should be structured. In Schema, there are different controls and each control has a property called props in which we can add attributes like minlength, maxlength, required, disabled, pattern etc.

To illustrate schema level validations, see the code snippet and explanation below.
```
const vehicleInfoModel = (index) => {
  return [{
      key: "ManualVehicleDetails",
      type: "Card",
      title: "VEHICLE INFORMATION",
      className: "container",
      titleClassName: "commonHead",
      childsClassName: "",
      controls: [
        {
          key: "vehiclevin",
          label: "VEHICLE VIN*",
          props: {
            required: true, 
            maxlength: 17, 
            placeholder: 'Please enter VIN number 17 alphanumeric characters', 
            pattern : "[A-Za-z0-9]{17}" 
          },
          labelClass: "col-md-2 mt-3",
          inputClass: "col-md-4 mt-3",
          positionClass: "col-md-6",
          isColummnDisplay: true,
          dataPath: "Risks.Vehicles." + index + ".VIN",
        }
      ]
    }]
};
export default vehicleInfoModel;
```
When user will submit the form, if Vehicle VIN format is not according to the given pattern or user has not filled any value in that field than it will throw an error. 
Also if we want to add our own error message then add below code after props.
```
errorMessage: "Please enter VIN",
```

### Field level validations

Field level validations are passed into the onChange method inside of ``Dynamicform`` component. onChange event will be triggered as soon as the user changes the text without waiting for the user to focus out.

To illustrate field level validations, see the code snippet and explanation below.
```
const onChange = (changedSchema, key) => {
    if (key == "vehiclevin") {
         if (checkDuplicateVehicle(vehicleInfo, changedSchema.Risks.Vehicles[currentIndex], currentIndex)) {
            toast.error("VIN# already added");
        }
    }
    else if (key == "year") {
        changedSchema.Risks.Vehicles[currentIndex].VehicleAge = (parseInt((new Date()).getFullYear()) - parseInt(changedSchema.Risks.Vehicles[currentIndex].Year)).toString();
    }
    setVehicleInfo(changedSchema);
}
```
Here, changedSchema is the data model and key is the field on which user is performing some action.

### Form level validations

Form level validations are passed into the onSubmit method inside of ``Dynamicform`` component. onSubmit is an event handler attached to the form submission event.

To illustrate form level validations, see the code snippet and explanation below.

```
const onSubmit = async (e) => {
    e.preventDefault();
    const currentPolicy = getStoreState(storeKeys.PolicyReducer);
    let resp = validateVehicles(currentPolicy);
    if (resp?.Errors?.length != 0) {
        for (var i = 1; i < resp.Errors.length; i++) 
            toast.error(resp.Errors[i]);
        return false;
    }
    else {
        await save(currentPolicy, commonKeys.EmptyString, routeKeys.ApplicationVehicleInfo, commonKeys.EmptyString, progressBarMapKeys.VehicleInfo);
        router.push(routeKeys.ApplicationIneligibleInfo.toLowerCase());
    }
};
```

### Validators

Validators are used to validate the input for any particular field. These are passed into the validators variables array inside of ``Dynamicform`` component. The image below shows different validators we have created.

>![Validators](../../static/img/docs/diep2/ui_validators.png)

These validators contain the logic for verifying different input crucial to business using different third party services too, like different API can be used for Vehicle Identification Number and Driver License Number verification. These validation trigger and shows a toast with specific message defined in the body of every validation object passed into the validators variable inside dynamicform component; on schema change or on submission of form.

To illustrate Validators, see the code snippet and explanation below.
```
//Sample code for VIN validation
const VINValidator = (input) => {
  return (input != null) && (input?.length == 17) && !(input?.indexOf(' ') >= 0);
}
export default VINValidator;
```

```
//Sample code for use of validators
<DynamicForm
    key="vehicleInfo"
    formId="vehicleInfo"
    onChangeValidateForm="true"
    positionClass="form"
    titlePositionClass="form-title"
    formPositionClass="dynamic-form"
    actionsPositionClass="form-actions"
    submitPositionClass="btnStyle btnReject float-right"
    defaultValues={vehicleInfo}
    validators={[
        {
            key: "Risks.Vehicles." + (vehicleInfo.Risks?.Vehicles?.length > 0 ? currentIndex : 0) + ".VIN",
            validations: [{
                "validator": Validator.VINValidator,
                "message": "Please enter valid VIN"
            }]
        },                        
    ]}
    model={vehicleInfoSchema}
    dataModel={vehicleInfo}
    onSubmit={(model, e) => {
        onSubmit(model, e);
    }}
    onChange={(model, key) => {
        onChange(model, key);
    }}                        
/>
```


