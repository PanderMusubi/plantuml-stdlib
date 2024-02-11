# plantuml-stdlib
Contains official Standard Library for PlantUML
See http://plantuml.com/stdlib for more information.

This Standard Library is included in official release of PlantUML.
Following the C convention for "C standard library" (see https://en.wikipedia.org/wiki/C_standard_library )

## AWS Icons

PlantUML images, sprites, macros, and other includes for Amazon Web Services (AWS) services and resources. Used to create PlantUML diagrams with AWS components. All elements are generated from the official [AWS Architecture Icons](https://aws.amazon.com/architecture/icons/) and when combined with [PlantUML](http://plantuml.com/) and the [C4 model](https://c4model.com/), are a great way to communicate your design, deployment, and topology as code.

Besides usage as custom sprites on PlantUML components, different types of diagrams can quickly and easily be created with the icons.

More info on [awslabs github account](https://github.com/awslabs/aws-icons-for-plantuml).

## AWS library

The AWS library consists of Amazon AWS icons, it provides icons of two different sizes.

Use it by including the file that contains the sprite, eg: `!include <aws/Storage/AmazonS3/AmazonS3>`.
When imported, you can use the sprite as normally you would, using `<$sprite_name>`.

You may also include the `common.puml` file, eg: `!include <aws/common>`, which contains helper macros defined.
With the `common.puml` imported, you can use the `NAME_OF_SPRITE(parameters...)` macro.

Example of usage:
```
@startuml
!include <aws/common>
!include <aws/Storage/AmazonS3/AmazonS3>
!include <aws/Storage/AmazonS3/bucket/bucket>

AMAZONS3(s3_internal)
AMAZONS3(s3_partner,"Vendor's S3")
s3_internal <- s3_partner
@enduml
```

This example renders the following image:

![Example](http://www.plantuml.com/plantuml/png/SoWkIImgAStDuLBCp4lEAKr9LR19B2_MJyxFpStFiqCJ3Ix9BqfCJzLtp4sioiyBDeOp22fCAatEJYs1KdPSN8w-Zb7-Vi766iN6yPbv9Qb5UOavcYYY1K1tvQKMwIY5fUQbv1Uf5oi46ojfSY6fLx3HLK0ev780gWDw1000 "Example")

## Azure library

The Azure library consists of Microsoft Azure icons.

Use it by including the file that contains the sprite, eg: `!include <azure/Analytics/AzureEventHub.puml>`.
When imported, you can use the sprite as normally you would, using `<$sprite_name>`.

You may also include the `AzureCommon.puml` file, eg: `!include <azure/AzureCommon.puml>`, which contains helper macros defined.
With the `azure/AzureCommon.puml` imported, you can use the `NAME_OF_SPRITE(parameters...)` macro.

Example of usage:
```
@startuml
!include <azure/AzureCommon>
!include <azure/Analytics/AzureEventHub>
!include <azure/Analytics/AzureStreamAnalyticsJob>
!include <azure/Databases/AzureCosmosDb>

left to right direction

agent "Device Simulator" as devices #fff

AzureEventHub(fareDataEventHub, "Fare Data", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureEventHub(tripDataEventHub, "Trip Data", "PK: Medallion HackLicense VendorId; 3 TUs")
AzureStreamAnalyticsJob(streamAnalytics, "Stream Processing", "6 SUs")
AzureCosmosDb(outputCosmosDb, "Output Database", "1,000 RUs")

devices --> fareDataEventHub
devices --> tripDataEventHub
fareDataEventHub --> streamAnalytics
tripDataEventHub --> streamAnalytics
streamAnalytics --> outputCosmosDb

@enduml
```

This example renders the following image:

![Example](http://www.plantuml.com/plantuml/proxy?idx=0&src=https%3A%2F%2Fraw.githubusercontent.com%2FRicardoNiepel%2FAzure-PlantUML%2Fmaster%2Fsamples%2FBasic%2520usage%2520-%2520Stream%2520processing%2520with%2520Azure%2520Stream%2520Analytics.puml "Example")

## C4 library (C4-PlantUML)

The C4 library enables a simple way of describing and communicate software architectures with an intuitive language.

It is the PlantUML integrated version of [C4-PlantUML](https://github.com/plantuml-stdlib/C4-PlantUML) and has the big advantage that it can be used without additional external includes.
(E.g. container diagrams can be drawn with `!include <C4/C4_Container>` and no `!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml` is required.)

Example of usage:

```plantuml
@startuml
!include <C4/C4_Container>

Person(admin, "Administrator")
System_Boundary(c1, "Sample System") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")

SHOW_LEGEND()
@enduml
```

This example renders the following image:

[![Example](https://www.plantuml.com/plantuml/png/JOzVIyCm5CNVyockzQM3CPdiKMIrbkr1Px7LFPQilK8WVq9oGndYT_UMpSsyN9BpE-UUh2F9GCbeSQDihzE0y52kxifLLpfBKbaCZqBK6AApkHoCidF8YccgI46I2zbCDCT8QBedb-mWmp7lbmmrqdYDSDAo6NmBu7D9pKSyTD9x9lTuWC9xhNf9ojcCdyhREHHDlTXLBLi2mlrY2Q-VvQGLMhinGefS2iX1xuoNZ9YaIKqhsr4HOG1I1ZNlYbpnvrmofvF8EMUCHV6E-kzprreVaPqyjsrRDqnDq4MzncoG8bzn6b_1cVyMqMpVzjrBjQbsp_bChD4EoUXV)](https://www.plantuml.com/plantuml/uml/JOzVIyCm5CNVyockzQM3CPdiKMIrbkr1Px7LFPQilK8WVq9oGndYT_UMpSsyN9BpE-UUh2F9GCbeSQDihzE0y52kxifLLpfBKbaCZqBK6AApkHoCidF8YccgI46I2zbCDCT8QBedb-mWmp7lbmmrqdYDSDAo6NmBu7D9pKSyTD9x9lTuWC9xhNf9ojcCdyhREHHDlTXLBLi2mlrY2Q-VvQGLMhinGefS2iX1xuoNZ9YaIKqhsr4HOG1I1ZNlYbpnvrmofvF8EMUCHV6E-kzprreVaPqyjsrRDqnDq4MzncoG8bzn6b_1cVyMqMpVzjrBjQbsp_bChD4EoUXV)

## Classy library

The Classy library allows for using an Object Oriented approach to diagramming
in PlantUML.

That is to say that it allows you to define and instantiate your own classes as
well as allow you to call methods defined on those classes. You can also inherit
from one or more classes where desired.

Use it by including the file that contains the Classy class that you want to use
within your diagram. Alternatively, if you want to define your own type, you can
just include the `core.puml` file, eg: `!include <classy/core>`, which contains
all of the necessary functions.

Example of usage:
```
@startuml

    !include <classy/core>

    $class(HelloWorld)
      $classVar(msg, string, "Hello World!")

      $classMethod(getMessage)
        !function HelloWorld__getMessage($this)
          !return $getInstanceVar($this, 'msg')
        !endfunction
      $endclassMethod(getMessage)

      $classMethod(setMessage)
        !function HelloWorld__setMessage($this, $args)
          $setInstanceVar($this, 'msg', $call($args, 'each'))
          !return $this
        !endfunction
      $endclassMethod(setMessage)
    $endclass(HelloWorld)

    !$hello = $new(HelloWorld)
    Alice -> Bob : $call($hello, 'getMessage')

    $call($hello, 'setMessage', array($new(array), '2nd message!'), $void=%true())

    Alice -> Bob : $call($hello, 'getMessage')

@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/SoWkIImgAStDuNBAJrBGjLDmpCbCJbMmKl18pSd9LmZFByf9KKINCyfBKSXDBIvEJ4zLKEHoICrB0He00000)

## Classy C4 library

The Classy C4 library combines the Classy and C4 libraries by defining Classy
classes that wrap the C4 macros.

Example of usage:
```
@startuml

    !include <classy-c4/container>
    !include <classy-c4/person>
    !include <classy-c4/system>

    !$system = $new(System)
    $call($system, 'setName', 'Label', $void=%true())
    $call($system, 'setDescription', 'Optional Description', $void=%true())

    !$person = $new(Person)
    $call($person, 'setName', 'Label', $void=%true())
    $call($person, 'setDescription', 'Optional Description', $void=%true())

    !$container = $new(Container)
    $call($container, 'setName', 'Label', $void=%true())
    $call($container, 'setDescription', 'Optional Description', $void=%true())
    $call($container, 'setTechnology', 'Technology', $void=%true())

    !$personAlias = $call($person, 'render')
    !$containerAlias = $call($container, 'render')
    $call($system, 'render', $void=%true())

    Rel($personAlias, $containerAlias, "Label", "Optional Technology")

@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/ZOvFIyGm4CNl-HIrfowupMLFdbQgjnKN_vnbcWxRm6GICXDalxtPWaKHnTDxCypxpTkBGjOIg1bsR_U40Ld5N7bsL2PiPjKaDzPcUEzFNkSo5i7i8YkozYu6cmZuaj-AJkH7E-osnylgzU5W0uXYjfKyr0HunjodUclC4RD4xj8Yj-H1hfls02DIMyrZKXyPgBb3STalKxinAwHpd-v7z0NTp97YwVm7wFaiYg6JHVxxtJmXVI-yjlWTyQNEnkoHfnBe0m00)

## Elastic library

The Elastic library consists of [Elastic](https://www.elastic.co) icons.
It is similar in use to the AWS and Azure libraries (it used the same tool to create them).

Use it by including the file that contains the sprite, eg: `!include <elastic/elasticsearch/elasticsearch.puml>`.
When imported, you can use the sprite as normally you would, using `<$sprite_name>`.

You may also include the `common.puml` file, eg: `!include <elastic/common>`, which contains helper macros defined.
With the `common.puml` imported, you can use the `NAME_OF_SPRITE(parameters...)` macro.

Example of usage:
```
@startuml
    !include <elastic/common>
    !include <elastic/elasticsearch/elasticsearch>
    !include <elastic/logstash/logstash>
    !include <elastic/kibana/kibana>

    ELASTICSEARCH(ElasticSearch, "Search and Analyze",database)
    LOGSTASH(Logstash, "Parse and Transform",node)
    KIBANA(Kibana, "Visualize",agent) 
    
    Logstash -right-> ElasticSearch: Transformed Data
    ElasticSearch -right-> Kibana: Data to View

@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/TOxFQiCm38VlUGejfnHITYyZrEl2MXgsCOVUrLXBpFm7R8UnFVrI9oNa41yi6N-VVjhxW2xqMYKmd0Tf6jKBWYTIw8Di7XkhjJN5okzKFQ5hkkLhJL6szG5zTszMmMzvHODJAP98bHNZzUd0I_PvE6RbIFAObqCwDe1603EeVlyepGK6lAAdJVIhzrTUCtxCgYbyi3xGUOfIxT3uB-jqcXih9kLyUcPlB3l7DGRy8dsFIjvcOqicR21YyRfFXQsJRHUs1InMtCq99E050qPhmSpgcBYB70GB5qa_IR8d8tgj_W40)

## Tupadr3 library

This library contains several libraries of icons (including Devicons and Font Awesome )

Use it by including the file that contains the sprite, eg: `!include <tupadr3/font-awesome/align_center>`.
When imported, you can use the sprite as normally you would, using `<$sprite_name>`.

You may also include the `common.puml` file, eg: `!include <tupadr3/common>`, which contains helper macros defined.
With the `common.puml` imported, you can use the `NAME_OF_SPRITE(parameters...)` macro.

Example of usage:
```
@startuml
!include <tupadr3/common>
!include <tupadr3/font-awesome/server>
!include <tupadr3/font-awesome/database>

title Styling example

FA_SERVER(web1,web1) #Green
FA_SERVER(web2,web2) #Yellow
FA_SERVER(web3,web3) #Blue
FA_SERVER(web4,web4) #YellowGreen

FA_DATABASE(db1,LIVE,database,white) #RoyalBlue
FA_DATABASE(db2,SPARE,database) #Red

db1 <--> db2

web1 <--> db1
web2 <--> db1
web3 <--> db1
web4 <--> db1
@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/XOvHIyCm58NVyolkyC49hMNjdcICTTZ9OC9eTU2JfCjr2wH9QMwj-_ScpbagWY-1mtU-axkmn1jgAyMkOQkufkV73LWIIfQWJGTIxrKhqC9wRtIuCfgWg1j9Q4TG8CAHgBPtKNIGT6pBsxsf8cfhBfeagjsSNmwbLz-S6jgpojZeUnTcbxOpAwFdVv0latTeJOMHnUOTctzhWXClkSKvOoH98HHqKb8V03zuLIjaR9M-5bc-o_9nX-KayCyDN3qqY7h8OizYnrvGATCDOU9Xuk1IjJX4Ku-cFzvvsLVkqwTqcHRPMBX_D-jT5bok3RgZ97HARavS-SbV_JWejcdU2xwAWZ6t1BCmd8EhCDPX7oS-nOEK3DAqJmlKegtK9m00 "Example")

## Google Material Icons

This library consists of a free Material style icons from Google and other artists.

Use it by including the file that contains the sprite, eg: `!include <material/ma_folder_move>`.
When imported, you can use the sprite as normally you would, using `<$ma_sprite_name>`.
Notice that this library requires an `ma_` preffix on sprites names, this is to avoid clash of names if multiple sprites have the same name on different libraries.

You may also include the `common.puml` file, eg: `!include <material/common>`, which contains helper macros defined.
With the `common.puml` imported, you can use the `MA_NAME_OF_SPRITE(parameters...)` macro, note again the use of the prefix `MA_`.

Example of usage:
```
@startuml
!include <material/common>
' To import the sprite file you DON'T need to place a prefix!
!include <material/folder_move>

MA_FOLDER_MOVE(Red, 1, dir, rectangle, "A label")
@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/PSn12i8m40NGVK_nsqqL0k9U2eNMbRLGYjiIawa69faGKz7RUm3V0LxfWk7D4avUPqfEyy68znAQeiOiS3vAoiXFmYicbmchOy9NDdJZjPuHY2oo8B8s18sOQ7MViYZ_urNOKbgylAafYg5TpkEbwwTb66_zRYAhS5ImBYaaCbc71vD2rOBrdRZQ_m00 "Example")

## Domain Story library

This library provides a set of macros to easily describe and document a domain story which was developed in
a [Domain Storytelling](http://www.domainstorytelling.org) workshop.

For more usage instructions see [DomainStory-PlantUML](https://github.com/johthor/DomainStory-PlantUML).

Example of usage:

```
@startuml
!include <DomainStory/domainStory>

Boundary(System) {
    Person(Alice)
    Conversation(weather)
    Person(Bob)
}

activity(1, Alice, talks about the, weather, with, Bob)
@enduml
```

This example renders the following image:

![Example](http://www.plantuml.com/plantuml/png/JSx1IWGn30RWUv-YtcPWdEBLqxfwL5XOV81C9zXg9rdQlxiCuhlR7GGtf_0bVyYkW3BgainT59_gp3O0f_BeNARB-14HwbGBPwy25enU5_Uf0K6pUz65eXoXURq_91AylxswAxdvVpAUhjVDNglCbDVkk1RmqjjlOriTE1ULxYb5p_qcpohdXeJO_CA4mBc_tTthr9iVOyWZdYFMxc6mMtwmeFHLB4rQOH4Q_ELR4n46kqLtB7DxwHS0
 "Example")

## Notes

When mixing sprites macros with other elements you may get a syntax error if, for example, trying to add a rectangle along with classes.
In those cases, add `{` and `}` after the macro to create the empty rectangle.

Example of usage:
```
@startuml
!include <material/common>
' To import the sprite file you DON'T need to place a prefix!
!include <material/folder_move>

MA_FOLDER_MOVE(Red, 1, dir, rectangle, "A label") {
}

class foo {
    bar
}
@enduml
```

This example renders the following image:
![Example](http://www.plantuml.com/plantuml/png/ROz1Yi9044NtVOgl6sSW8Eu7KT1PJGm4SHlAxeesL7U5IaUKOUu-EO1_zzxYmT-DXQnCITmYPYzJO7mbAcoHPEqr9SrRjy9P4TEWLb3kZ76mM1Xz5CPB9noQq-gCp1nG58EGPn06upu-5-_2lKfWwv8-UEjSlU--cv_3iUtgvdByQ3bKs5G8qIeO-qBv9bnXkOVGbMNvYL_tvvmN6aVqgZDYtfLirZlEORxp3m00 "Example")


## Sources

* **aws**: made by https://github.com/milo-minderbinder/AWS-PlantUML
* **classy**: made by https://github.com/james-gadrow-kr/classy-plantuml
* **classy-c4**: made by https://github.com/james-gadrow-kr/classy-c4
* **tupadr3**: made by https://github.com/tupadr3/plantuml-icon-font-sprites
* **Material Icons**: from https://github.com/Templarian/MaterialDesign
* **Elastic Icons**: from https://github.com/Crashedmind/PlantUML-Elastic-icons
* **Domain Story**: from https://github.com/johthor/DomainStory-PlantUML

You can create Pull Request to update or add some library here if you find it relevant.
