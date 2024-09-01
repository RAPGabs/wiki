---

id: usingApolloServer

title: Using Apollo Server

---

Follow the mentioned steps:-

1. Search for `NEXT_PUBLIC_GQL_END_POINT` in you **.env.local** file.
2. Copy the URL and browse the URL.
3. Press on **Query your server**.
4. You'll see a sceen like 
>![Apollo_Server_Main_Page](../../static/img/docs/usingapolloserver/ApolloServerMainPage.png)
- The Green glow in corner indicates your function is ready to use.
5. Now select Query if you want to query the DB, for modifying data or creating new data select Mutation option.
6. When you select Query in the left pane you'll see a list of queries.
7. Select which query you want to perform.
8. After selecting the Query you can select the fields you want to get from DB from the **Fields section**.
9. Select input from Arguments section. In the bottom section inside **Variables** tab you'll see the input object formed.
10. Select all the input and pass the corresponding values.
11. Click on Query button in Operation section.
12. If all your parameters are correct you'll see the result in right **Response** section.

Example

1. ENGS Dev GQL Endpoint :- `https://devengsgql.azurewebsites.net/api/PolicyGraphQL?`
2. Sample Query
```bash
query QueryByContainer($client: String, $containerId: String) {
  queryByContainer(client: $client, containerId: $containerId) {
    Client
    Code
    Name
    Status
    Products
    Reference
    Role
    JWTstring
    Details {
      Contact {
        HomePhone
        BusinessPhone
        Fax
        MobilePhone
        SendSms
        EmailId
      }
      Address {
        AddressType
        StreetName
        Zip
        City
        County
        State
        Addr2
      }
    }
  }
}
```
3. Sample Input
```bash
{
  "client": "ENGS",
  "containerId": "agents"
}
```

4. Sample Response
```bash
{
  "data": {
    "queryByContainer": [
      {
        "Client": "ENGS",
        "Code": "13531",
        "Name": "Maria Fonseca",
        "Status": "Active",
        "Products": [
          "ENGS1IL"
        ],
        "Reference": [
          "101001"
        ],
        "Role": null,
        "JWTstring": null,
        "Details": {
          "Contact": {
            "HomePhone": "0XX-XXX-XX",
            "BusinessPhone": "+919599400141",
            "Fax": "0XX-XXX-XX00",
            "MobilePhone": "0XX-XXX-XX",
            "SendSms": false,
            "EmailId": "msingh@cogitate.us"
          },
          "Address": {
            "AddressType": "M",
            "StreetName": "1904 Leland Dr,",
            "Zip": "3XX-XXX-XX",
            "City": "MXX-XXX-XXta",
            "County": "CXX-XXX-XXBB",
            "State": "CA",
            "Addr2": "1XXXXXXXXS"
          }
        }
      },
      {
        "Client": "ENGS",
        "Code": "12912",
        "Name": "Deon Duff",
        "Status": "Active",
        "Products": [
          "ENGS1IL"
        ],
        "Reference": [
          "101001"
        ],
        "Role": null,
        "JWTstring": null,
        "Details": {
          "Contact": {
            "HomePhone": "0XX-XXX-XX",
            "BusinessPhone": "+919599400141",
            "Fax": "0XX-XXX-XX00",
            "MobilePhone": "0XX-XXX-XX",
            "SendSms": false,
            "EmailId": "msingh@cogitate.us"
          },
          "Address": {
            "AddressType": "M",
            "StreetName": "1904 Leland Dr,",
            "Zip": "3XX-XXX-XX",
            "City": "MXX-XXX-XXta",
            "County": "CXX-XXX-XXBB",
            "State": "CA",
            "Addr2": "1XXXXXXXXS"
          }
        }
      }
    ]
  }
}
```
