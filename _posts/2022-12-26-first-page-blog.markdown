---
layout: "post"
title: "This is the first blog"
---

<!-- layout.author -->
There are cases where a client may request to create new fields, or to modify existing fields in regard to their business needs. In such scenarios, one needs to proceed with certain steps to make the necessary changes in keeping a view of which version the originator comes into. This report documents the procedure for the v1 clients such as `finnable,krazybee,etc.`

## 1. Updating the existing fields
When a client requests for the updation of the existing fields, ensure that the field modification has no effect on the other investors as the fields in the V1 clients are universal for the investors for that particular originator. Hence, Get clarification on whether a field can be updated from the implementation team. Once approval has been granted to do so, start working on it.

One of the tasks could be that the clients can ask to make a field mandatory or optional. In such cases, the following file has to be modified - `“app/models/concerns/viv_colending_api/constants/unprocessed_data/{{originator}}/loan.rb”.` This file consists of all the fields for the particular originator. Find the required fields that need to be made changes to and make the required: true/false based on the requirement. Similarly, any changes in the behavior of fields is advisable to be done in this particular file.

When there is a need for introducing the validations/mappings related to the existing fields proposed by the clients, the code for the required tasks has to be written in the file - `“app/models/viv_colending_api/unprocessed_data/ {{originator}}/loan.rb”.` 

## 2. Creation of new fields
The creation of new fields can be requested from the clients, in that particular case we need to follow the proper steps to ensure that the fields are introduced to the platform that satisfy the business requirements of the clients.

For the V1 clients, as stated above, the fields are universal for all the investors, hence they need to be added in the file- `“app/models/concerns/ viv_colending_api/constants/unprocessed_data/{{originator}}/loan.rb”.` When the field is added to the file, make sure that the field is also added to the “detailed_loan_info.json.jbuilder” in the appropriate section. In case, the new field that is being added relates to the borrower, make sure that the field name is also added to the file- `“detailed_borrower_info.json.jbuilder”.`

After adding the field details to the aforementioned files, any validations or mapping, if any, are to be written in the file - `“app/models/viv_colending_api/ unprocessed_data/ {{originator}}/loan.rb”.`

For the v1 clients, since there is customization option to the originators, there can be discrepancies between the field provided by the client and the fields that have to be added to the platform, hence make sure that the mapping is properly done on the product_configuration table. Whenever there is a new field addition, write a data_migration file to update the mapping of the loan/borrower with the new field and make sure the format is being preserved so as to not throw errors.
            




[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
