
FORMAT: 1A
HOST: https://main.trakto.io/api/v1

# Trakto Button & API 

<img src="https://trakto.design/img/editor/01.Trakto.png" width=100%>

# Concepts

| Term              | What's is this 
|---                |--- 
|**Trakto Button®** | Tool that visually integrates the editor with your application
|**API**            | Tool that manages documents and templates available to your user
|**Templates**      | It's a predefined document that can be copied so that someone can edit it through the editor. 
|**Formats**        | Are descriptions of pages that are used to create new documents or arts through the editor.
|**Documents**      | They are materials created through the editor, for example the arts for social networks.

#Requirements

To use, the API requires:

1. **API Secret**: Unique and secret key available in your Trakto's Admin platform;
2. **Product Key**: Public key used for your product in editor embed;
3. **User Token**: User Id available via API and Trakto Button®;
4. **Origin**: Allowed URL for API usage.

# URLs Source

## Live mode
| Tool  | URL                                        |
|-------|--------------------------------------------|
|**Sdk**| https://sdk.trakto.io/trakto-editor.min.js |
|**API**| https://main.trakto.io/api/v1/             |

## Test mode
| Tool  | URL                                        |
|-------|--------------------------------------------|
|**Sdk**| Coming Soon                                |
|**API**| Coming Soon                                |

# Samples

1. See our sample project in **Github**: https://github.com/trakto/trakto-sdk-sample
2. See the button in **action**: https://sdk-sample-page.web.app/

# Trakto Button®

The Trakto Button® allows the Trakto editor to be used within your application.

The editor is made available according to the look of your website and with totally customized content for your customers.

**[Watch the video of the button in operation](https://cdn-std.dprcdn.net/files/acc_632271/NuzGtr)**

# Step by step for use the Trakto Button®

The image below shows the datailed flow of button operation when integrated into your platform.

<img src="https://camo.githubusercontent.com/ed2ff0031816864a53ef013e9e5fde4b6c9f15c2/68747470733a2f2f666972656261736573746f726167652e676f6f676c65617069732e636f6d2f76302f622f7472616b746f2d6465762e61707073706f742e636f6d2f6f2f6465765f6173736574732532465472616b746f253230427574746f6e25323053444b2e6a70673f616c743d6d6564696126746f6b656e3d38313463663264622d333237352d346564662d396635392d313830653464363462383061" width=100%>


## Import the sdk

```
    <script src="https://sdk.trakto.io/trakto-editor.min.js"></script>
```

## Initialize the sdk

```js 
 <script>
    window.onload = () => {
        (function() {
            TraktoEditor.init({
                apiSecret: '<Your Api Key>',
                productKey: '<Your Product Key>',
                userEmail: 'user@email.com', 
                buttonClassName: 'trakto-button', 
                defaultCallback: data => {  },
                listFormatsCallback: (data) => { },
                listTemplatesCallback: (data) => { },
                listDocumentsCallback: (data) => { }
            });
        })();
    };
</script>
```

**Note:** 
> Trakto takes care of the entire process of authenticating its users with editor.


### About callbacks

|Fields                    |Description                                                                                                                |Required|
|--------------------------|---------------------------------------------------------------------------------------------------------------------------|--------|
|**buttonClassName**       |Used to stylize the look of the button according to its application                                                        |Required|
|**defaultCallback**       |Callback executed after document completion in Trakto Editor. Returns the address of the images for the finished document. |Required|
|**listFormatsCallback**   |Callback executed to return all available page formats to your editor.                                                     |Optional|
|**listTemplatesCallback** |Callback executed to return all available templates to your editor                                                         |Optional|
|**listDocumentsCallback** |Callback executed to return all users documents available                                                                  |Optional|

Callbacks return the following data structures:

#### Templates (listTemplatesCallback)

```JSON
{
    [
        {
            "id": "nT1j4cCle3L2hCs",
            "title": "Template",
            "printable": false,
            "tags": ["tag1", "tag2", "tag3"],
            "theme_reference": "M4S8KfaL7Fi0uSbfYFYF",
            "pages": [
                {
                    "page_index": 0,
                    "page_format_id": "H6BWnAc27l8hMvbItcmJ"
                }
            ],
            "page_format_reference": "H6BWnAc27l8hMvbItcmJ",
            "cover": {
                "regular": "https://xyz.trakto.io/abcd.png",
                "low": "https://xyz.trakto.io/1234.png",
                "medium": "https://xyz.trakto.io/qwerty.png",
                "high": "https://xyz.trakto.io/zxcvb.png",
                "raw": "https://xyz.trakto.io/asdfg.png"
            },
            "thumbs": {
                "regular": "https://xyz.trakto.io/abcd.png",
                "low": "https://xyz.trakto.io/1234.png",
                "medium": "https://xyz.trakto.io/qwerty.png",
                "high": "https://xyz.trakto.io/zxcvb.png",
                "raw": "https://xyz.trakto.io/asdfg.png"
            },
            "created_at": "2019-05-10T12:41:24.018Z",
            "updated_at": "2019-05-10T12:41:24.018Z"
        }
    ]
}
```

| Attribute         |Type       | Description
|---                |---        | ---
|**id**             | String    | Templates's id. This field is unique
|**created_at**     | Date      | Date the document was created.
|**thumb**          | Object    | Image of the first page of the Template that was created by the user.
|**regular**        | String    | Thumb with regular quality.
|**low**            | String    | Thumb with regular low.
|**medium**         | String    | Thumb with regular medium.
|**height**         | String    | Thumb with regular high.
|**page_index**     | Number    | Represents the index (order number) of the page in the document.
|**page_format_id** | String    | Page's format identifier.

#### Formats (listFormatsCallback)

```JSON
{
    [
          {
            "id": "IVGTOocCRgmT1F0",
            "title": "Page Format 1",
            "canva_dimension": {
                "height": 234,
                "width": 234,
                "unit": "px"
            },
            "thumbs": {
                "regular": "https://xyz.trakto.io/abcd.png",
                "low": "https://xyz.trakto.io/1234.png",
                "medium": "https://xyz.trakto.io/qwerty.png",
                "high": "https://xyz.trakto.io/zxcvb.png",
                "raw": "https://xyz.trakto.io/asdfg.png"
            },
            "created_at": "2019-07-18T18:35:09.418Z",
            "updated_at": "2019-07-18T18:35:33.981Z"
          }
    ]
}
```

| Attribute         |Type       | Description
|---                |---        | ---
|**id**             | String    | Template's identifier.
|**created_at**     | Date      | Date the template was created.
|**updated_at**     | Date      | Last date that template was updated.
|**deleted_at**     | Date      | Template deleted date.
|**title**          | String    | Title of Template.
|**is_published**   | Boolean   | Identifies whether the template is available for use by users 
|**published_at**   | Date      | Date of availability
|**Thumb**          | Object    | Image of the first page of the template that was created by the user.
|**Cover**          | Object    | Promotional Image
|**regular**        | String    | Thumb with regular quality
|**low**            | String    | Thumb with regular low
|**medium**         | String    | Thumb with regular medium
|**hight**          | String    | Thumb with regular high
|**printable**      | Boolean   | Identifies whether print clipping marks are enabled
|**page_index**     | Number    | Represents the index (order number) of the page in the document
|**page_format_id** | String    | Page's format identifier


#### listDocumentsCallback (user's documents)

```JSON
    [
        {
            "user_id": "59YvyzoCi0IMS7xybbRG",
            "document_id": "daOOI88dbbRG",
            "created_at": "2019-07-11T12:18:33.179Z", 
            "updated_at": "2019-07-11T12:18:33.179Z",
            "pages":[
                    {   
                        {
                            "page_index": 0,
                            "page_format_id": "stehrsxvgm"
                            "thumb":{
                                "regular": "https://xyz.trakto.io/abcd.png",
                                "low": "https://xyz.trakto.io/1234.png",
                                "medium": "https://xyz.trakto.io/qwerty.png",
                                "high": "https://xyz.trakto.io/zxcvb.png",
                                "raw": "https://xyz.trakto.io/asdfg.png"
                            }
                        },
                        {   
                            "page_index": 1,
                            "page_format_id": "ldecjyiuqm",
                            "thumb":{
                                "regular": "https://xyz.trakto.io/abcd.png",
                                "low": "https://xyz.trakto.io/1234.png",
                                "medium": "https://xyz.trakto.io/qwerty.png",
                                "high": "https://xyz.trakto.io/zxcvb.png",
                                "raw": "https://xyz.trakto.io/asdfg.png"
                            }
                        }
                }
            ]
        }
    ]
```


| Attribute         |Type       | Description
|---                |---        | ---
|**user_id**        | String    | User's id. This field is unique
|**document_id**    | String    | Document's id. This field is unique
|**created_at**     | Date      | Date the document was created.
|**thumb**          | Object    | Image of the first page of the Template that was created by the user.
|**regular**        | String    | Thumb with regular quality.
|**low**            | String    | Thumb with regular low.
|**medium**         | String    | Thumb with regular medium.
|**height**         | String    | Thumb with regular high.
|**page_index**     | Number    | Represents the index (order number) of the page in the document.
|**page_format_id** | String    | Page's format identifier.


#### DefaultCallback (defaultCallback)

```JSON
    [
        {
            "user_id": "59YvyzoCi0IMS7xybbRG",
            "document_id": "daOOI88dbbRG",
            "created_at": "2019-07-11T12:18:33.179Z", 
            "updated_at": "2019-07-11T12:18:33.179Z",
            "pages":[
                    {   
                        {
                            "page_index": 0,
                            "page_format_id": "stehrsxvgm"
                            "thumb":{
                                "regular": "https://xyz.trakto.io/abcd.png",
                                "low": "https://xyz.trakto.io/1234.png",
                                "medium": "https://xyz.trakto.io/qwerty.png",
                                "high": "https://xyz.trakto.io/zxcvb.png",
                                "raw": "https://xyz.trakto.io/asdfg.png"
                            }
                        },
                        {   
                            "page_index": 1,
                            "page_format_id": "ldecjyiuqm",
                            "thumb":{
                                "regular": "https://xyz.trakto.io/abcd.png",
                                "low": "https://xyz.trakto.io/1234.png",
                                "medium": "https://xyz.trakto.io/qwerty.png",
                                "high": "https://xyz.trakto.io/zxcvb.png",
                                "raw": "https://xyz.trakto.io/asdfg.png"
                            }
                        }
                }
            ]
        }
    ]
```

| Attribute         |Type       | Description
|---                |---        | ---
|**user_id**        | String    | User's id. This field is unique
|**document_id**    | String    | Document's id. This field is unique
|**created_at**     | Date      | Date the document was created.
|**thumb**          | Object    | Image of the first page of the Template that was created by the user.
|**regular**        | String    | Thumb with regular quality.
|**low**            | String    | Thumb with regular low.
|**medium**         | String    | Thumb with regular medium.
|**height**         | String    | Thumb with regular high.
|**page_index**     | Number    | Represents the index (order number) of the page in the document.
|**page_format_id** | String    | Page's format identifier.

## Creating or editing a document

There are 3 ways to create and edit documents with the editor. For each of them, different button assignments are used:

### Creating from page format
```
    <button class="<Your Button Class Name>" data-formatid="<Your Format Id>"> 
        Your button title 
    </button>
```

### Creating from template
```
    <button class="<Your Button Class Name>" data-templateid="<Your Template Id>"> 
        Your button title 
    </button>
```

**c. Editing a document from user**
```
    <button class="<Your Button Class Name>" data-documentid="<Your Template Id>"> 
        Your button title 
    </button>
```

# Using the Rest API

All the enpdoints are enabled just in user context. Thus, the informations that will be used refers only to a user connected to his custom editor created with Trakto®

### List all Templates [/templates]

| Attribute         |Type       | Description
|---                |---        | ---
|**id**             | String    | Template's identifier.
|**created_at**     | Date      | Date the template was created.
|**updated_at**     | Date      | Last date that document was updated.
|**deleted_at**     | Date      | Template deleted date.
|**title**          | String    | Title defined by user.
|**thumb**          | Object    | Image of the first page of the Template that was created by the user.
|**cover**          | Object    | Promotional image.
|**regular**        | String    | Thumb with regular quality.
|**low**            | String    | Thumb with regular low.
|**medium**         | String    | Thumb with regular medium.
|**height**         | String    | Thumb with regular high.
|**printable**      | Boolean   | Identifies whether print clipping marks are enabled.
|**page_index**     | Number    | Represents the index (order number) of the page in the document.
|**page_format_id** | String    | Page's format identifier.

### Request [GET]

+ Request 

    + Header 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Response 200 (application/json)

        [
            {
                "id": "wgdksubqemheoqo",
                "created_at": "2019-07-11T12:18:33.179Z", 
                "updated_at": "2019-07-11T12:18:33.179Z",
                "published_at": "2019-07-11T12:18:33.179Z", 
                "is_published": true,
                "title": "Lorem Ipsum",
                "printable": false,
                "thumb": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "cover": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "pages":[
                    {   
                        "page_index": 0,
                        "page_format_id": "stehrsxvgm"
                    },
                    {   
                        "page_index": 1,
                        "format_id": "ldecjyiuqm"
                    }
                
                ]
            }
        ]


### Receive a Template from Id [/templates/{template_id}]


### Request [GET]

+ Request 

    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Parameters
    + template_id (required, string, `vbqaevoshnyuzss`) ... Template's ID
    

+ Response 200 (application/json)

            {
                "id": "wgdksubqemheoqo",
                "created_at": "2019-02-17T19:13:06.577Z",
                "updated_at": "2019-02-17T19:13:06.577Z",
                "published_at": "2019-02-17T19:13:06.577Z",
                "is_published": true,
                "title": "Lorem Ipsum",
                "printable": false,
                "thumb": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "cover": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "pages":[
                    {   
                        "page_index": 0,
                        "page_format_id": "stehrsxvgm"
                    },
                    {   
                        "page_index": 1,
                        "format_id": "ldecjyiuqm"
                    }
            }
## List all Formats [/formats]

This endpoint list all formats that can used for create a empty document.


| Attribute         |Type       | Description
|---                |---        | ---
|**id**             | String    | Template's identifier.
|**created_at**     | Date      | Date the template was created.
|**updated_at**     | Date      | Last date that template was updated.
|**deleted_at**     | Date      | Template deleted date.
|**title**          | String    | Title of Template.
|**is_published**   | Boolean   | Identifies whether the template is available for use by users 
|**published_at**   | Date      | Date of availability
|**Thumb**          | Object    | Image of the first page of the template that was created by the user.
|**Cover**          | Object    | Promotional Image
|**regular**        | String    | Thumb with regular quality
|**low**            | String    | Thumb with regular low
|**medium**         | String    | Thumb with regular medium
|**hight**          | String    | Thumb with regular high
|**printable**      | Boolean   | Identifies whether print clipping marks are enabled
|**page_index**     | Number    | Represents the index (order number) of the page in the document
|**page_format_id** | String    | Page's format identifier


### Request [GET]

+ Request 

    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Response 200 (application/json)

        [
            {
                "id": "pilezylzxvg",
                "created_at": "2019-07-11T12:18:33.179Z", 
                "updated_at": "2019-07-11T12:18:33.179Z",
                "title": "Social",
                "canva_dimension": {
                    "height": 480,
                    "width": 480,
                    "unit": "px"
                },
                "thumbs": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                }
            }
        ]

## Format from ID [/formats/{format_id}]


### Request [GET]

+ Request 

    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Parameters
    + format_id (required, string, `vbqaevoshnyuzss`) ... Page's format ID
    
+ Response 200 (application/json)

            {
                "id": "vbqaevoshnyuzss",
                "created_at": "2019-07-11T12:18:33.179Z", 
                "updated_at": "2019-07-11T12:18:33.179Z",
                "title": "Social",
                "canva_dimension": {
                    "height": 480,
                    "width": 480,
                    "unit": "px"
                },
                "thumbs": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                }
            }


## List all User's Documents [/documents]


| Attribute         |Type       | Description
|---                |---        | ---
|**id**             | String    | Document's identifier.
|**created_at**     | String    | Date the document was created.
|**updated_at**     | String    | Last date that document was updated.
|**deleted_at**     | String    | Document's deleted date document.
|**title**          | String    | Title defined by user.
|**Thumb**          | Object    | Image of the first page of the document that was created by the user.
|**regular**        | String    | Thumb with regular quality.
|**low**            | String    | Thumb with regular low.
|**medium**         | String    | Thumb with regular medium.
|**high**           | String    | Thumb with regular high.
|**printable**      | Boolean   | Identifies whether print clipping marks are enabled.
|**page_index**     | Number    | Represents the index (order number) of the page in the document.
|**page_format_id** | String    | Page's format identifier.


### Request [GET]

+ Request 
    
    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Response 200 (application/json)

        [
            {
                "id": "wgdksubqemheoqo",
                "created_at": "2019-07-11T12:18:33.179Z",
                "updated_at": "2019-07-11T12:18:33.179Z",
                "title": "Lorem Ipsum",
                "printable": false,
                "thumb": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "pages":[
                    {   
                        "page_index": 0,
                        "page_format_id": "stehrsxvgm"
                    },
                    {   
                        "page_index": 1,
                        "format_id": "ldecjyiuqm"
                    }
                
                ]
            }
        ]


## Create a copy of document [/documents/{document_id}/clone]
Creates a new copy of a user's document.

### Request [POST]

+ Parameters
    + document_id (required, string, `1lKM6m5gpL9Z9ZiV`) ... Document's ID

+ Request 

    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG
                
+ Response 200 (application/json)

        {
            "id": "wgdksubqemheoqo",
            "created_at": "2019-07-11T12:18:33.179Z",
            "updated_at": "2019-07-11T12:18:33.179Z",
            "title": "Lorem Ipsum",
            "printable": false,
            "thumb": { },
                "pages":[
                    {   
                        "page_index": 0,
                        "page_format_id": "stehrsxvgm"
                    }
                ]
        }


## Create a document from a template [/documents/create-from-template/{template_id}]
Creates a new document for the user using the contents of a template

### Request [POST]

+ Request 
    
    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Parameters
    + template_id (required, string, `1lKM6m5gpL9Z9ZiV`) ... Template's ID
    
+ Response 200 (application/json)

        [
            {
                "id": "wgdksubqemheoqo",
                "created_at": "2019-07-11T12:18:33.179Z",
                "updated_at": "2019-07-11T12:18:33.179Z",
                "title": "Lorem Ipsum",
                "printable": false,
                "thumbs": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "pages":[
                    {   
                        "page_index": 0,
                        "format_id": "stehrsxvgm"
                    },
                    {   
                        "page_index": 1,
                        "page_format_id": "ldecjyiuqm"
                    }
                
                ]
            }
        ]

## Create a document from Page Format [/documents/create-from-format/{page_format_id}]
### Request [POST]

+ Request 

    + Headers 

                Content-Type: application/json
                API-Secret: 59YvyzoCi0IMS7xybbRG
                User-Token: 0IMS7xybbRG
                Origin: 59YvyzoCi0IMS7xybbRG

+ Parameters
    + page_format_id (required, string, `1lKM6m5gpL9Z9ZiV`) ... Page format's ID
    
+ Response 200 (application/json)

        [
            {
                "id": "wgdksubqemheoqo",
                "created_at": "2019-07-11T12:18:33.179Z",
                "updated_at": "2019-07-11T12:18:33.179Z",
                "title": "Lorem Ipsum",
                "printable": false,
                "thumbs": {
                    "regular": "https://xyz.trakto.io/abcd.png",
                    "low": "https://xyz.trakto.io/1234.png",
                    "medium": "https://xyz.trakto.io/qwerty.png",
                    "high": "https://xyz.trakto.io/zxcvb.png",
                    "raw": "https://xyz.trakto.io/asdfg.png"
                },
                "pages":[
                    {   
                        "page_index": 0,
                        "format_id": "stehrsxvgm"
                    },
                    {   
                        "page_index": 1,
                        "page_format_id": "ldecjyiuqm"
                    }
                
                ]
            }
        ]
