<p align="center">
<img src="https://ebia.com.ec/assets/img/logo-black.png" height="200"/>
</p>

# EBIA ONBOARDING
***
This is for robust face detection and face recognition. This a Node.js wrapper library for the face detection and face recognition tools implemented from [Ebia Solutions](https://www.ebia.com.ec/).
***
## Table of Contents 📋
* **[Install](#install)**
* **[How to use](#how-to-use)**
* **[Example](#example)**
* **[Demo](#demo)**

<a name="install"></a>
# Install

##  AutoBuild - npm Component
Installing the package will build ebia-onboarding for you and download the models. Note, this might take some time.
``` bash
npm install ebia-onboarding
```

##  ManualBuild - Library
If you want to use an own build of <a href="https://www.ebia.com.ec/assets/rekognition/react-ebia.js"><b>ebia-onboarding</b></a> include this references:
``` javascript
<script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
<script crossorigin src="https://unpkg.com/prop-types@15.6.1/prop-types.js"></script>
<script crossorigin src="https://unpkg.com/babel-transform-in-browser@6.4.6/dist/btib.min.js"></script>
<script src="https://www.ebia.com.ec/assets/rekognition/react-ebia.js"></script>
```

<a name="how-to-use"></a>
# How to use

## For AutoBuild Component
``` javascript
import { EbiaOnboarding } from "ebia-onboarding";

```

## About Country
The functionality depends on the country.
For Ecuador, there is also the option of validation with the consulting Registro Civil Ecuador.
For other countries, it is necessary to send the photo for easy recognition.

### Face Recognition
#### Parameters
*  documento_identidad: It will ask you to upload a photograph of both the front and the back of the identity document.
*  servicio_basico: It will ask you to upload a basic service bill.
*  pais: (EC->Ecuador, BO->Bolivia)
*  prueba_vida: Options: PARPADEO, SONRISA, CARDINAL, BOSTEZO
*  cedula: National identity card number
*  nombres: First Name and Second Name
*  apellidos: First Last Name and Second Last Name
*  direccion: Address
*  foto: URL of the photograph to make the comparison.
*  letra_cedula: Font sizes of the titles for the capture of the photograph of the ID.
*  letra_prueba_vida: Size of the letter of the titles for the capture of the recognition
*  rekognitionSuccess: Successful response method.
*  rekognitionError: Error response method.
*  id_solicitud: Used to identify the process.
*  id_empresa: Company ID registered at ebia.com.ec
*  token: token generated with the input of the user, through api.
Only for Ecuador
*  rc: Use of query to Registro Civil Ecuador
*  huella: The first 6 digits of the fingerprint identifier. 

<a name="example"></a>
# Example

## Example of use without Registro Civil - AutoBuild Component
``` javascript
<EbiaOnboarding
            documento_identidad={false}
            servicio_basico={false}
            pais={"EC"}
            prueba_vida={"PARPADEO"}
            cedula={"1803231727"}
            nombres={"MONICA CECILIA"}
            apellidos={"BENAVIDES PINTO"}
            direccion={"DE LOS HIGOS E1076 Y DE LOS CIRUELOS"}
            foto={"https://elebus-rekognition.s3.amazonaws.com/personas/1710445097.jpg"}
            letra_cedula={70}
            letra_prueba_vida={40}
            rekognitionSuccess={rekognitionSuccess}
            rekognitionError={rekognitionError}
            id_solicitud={23}
            id_empresa={22}
            token={"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGVjayI6dHJ1ZSwiaWF0IjoxNjkxNTkyMjk1LCJleHAiOjE2OTE2Nzg2OTV9.b21NwICHH85Zm_e1lOLimsYsx8uo2BXvfPi1hShp97w"}
/>
```
## Example of use with Registro Civil - AutoBuild Component
``` javascript
<EbiaOnboarding
            cedula={"1803231727"}
            nombres={"MONICA CECILIA"}
	apellidos={"BENAVIDES PINTO"}
	rc={true}
	huella={"V2333E"}
	prueba_vida={"SONRISA"}
	letra_cedula={70}
	letra_prueba_vida={50}
	id_empresa={22}
	id_solicitud={123456}
	rekognitionSuccess={rekognitionSuccess}
            rekognitionError={rekognitionError}
	token={"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGVjayI6dHJ1ZSwiaWF0IjoxNjkxMDk2MjYwLCJleHAiOjE2OTExODI2NjB9.xumxrHfWcBpN89QYIbEgC5it3e_m_j-CbFiYMdZnFYY"}
/>
```
## Example of use with Registro Civil - ManualBuild Component
``` javascript
<Rekognition
	cedula={"1704759040"}
	nombres={"MARCO DIEGO "}
	apellidos={"ACOSTA VASQUEZ"}
	rc={true}
	huella={"V4443V"}
	prueba_vida={"SONRISA"}
	letra_cedula={70}
	letra_prueba_vida={50}
	id_empresa={22}
	id_solicitud={123456}
	rekognitionSuccess={rekognitionSuccess}
        rekognitionError={rekognitionError}
        token={"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjaGVjayI6dHJ1ZSwiaWF0IjoxNjkxMTU5NTU4LCJleHAiOjE2OTEyNDU5NTh9.sWYA1l8ZfMuebhq5PNGynko15JhzT--gDdjSUoXjWEw"}
				/>
```
example output (the lower the distance, the higher the similarity):
``` javascript
rekognitionSuccess (response)
data:
  {
    captura:"https://ebia-rekognition.s3.amazonaws.com/capturas/undefined/10566/R/1691684378072.jpg"
    rekognition: "eyJTaW1pbGFyaXR5Ijo5OS45OTk2ODcxOTQ4MjQyMiwiRmFjZSI6eyJCb3VuZGluZ0JveCI6eyJXaWR0aCI6MC4yNzMxNzM0ODEyMjU5Njc0LCJIZWlnaHQiOjAuMzgyODA2MzYwNzIxNTg4MTMsIkxlZnQiOjAuNDA3OTA5ODcwMTQ3NzA1MSwiVG9wIjowLjI4MTM2NDczODk0MTE5MjZ9LCJDb25maWRlbmNlIjo5OS45OTk3MjUzNDE3OTY4OCwiTGFuZG1hcmtzIjpbeyJUeXBlIjoiZXllTGVmdCIsIlgiOjAuNDk1NTQ3ODAxMjU2MTc5OCwiWSI6MC40MzY0MDI5NDY3MTA1ODY1NX0seyJUeXBlIjoiZXllUmlnaHQiLCJYIjowLjYxODk5MTQ5NDE3ODc3MiwiWSI6MC40MzM3OTExNjA1ODM0OTYxfSx7IlR5cGUiOiJtb3V0aExlZnQiLCJYIjowLjUxMjk3ODI1NTc0ODc0ODgsIlkiOjAuNTcyNDQ3Mjk5OTU3Mjc1NH0seyJUeXBlIjoibW91dGhSaWdodCIsIlgiOjAuNjE1NjQzNTYwODg2MzgzMSwiWSI6MC41NzAwOTU1MzkwOTMwMTc2fSx7IlR5cGUiOiJub3NlIiwiWCI6MC41NzA2NTc0OTE2ODM5NiwiWSI6MC40OTkzNDgwMTQ1OTMxMjQ0fV0sIlBvc2UiOnsiUm9sbCI6LTEuMzY0NTgyMDYxNzY3NTc4MSwiWWF3Ijo1LjA5ODc4NzMwNzczOTI1OCwiUGl0Y2giOjYuOTAyMDM2NjY2ODcwMTE3fSwiUXVhbGl0eSI6eyJCcmlnaHRuZXNzIjo3MC4zMzMyNTk1ODI1MTk1MywiU2hhcnBuZXNzIjo4OS44NTQ4MTI2MjIwNzAzMX19fQ=="
  }
```
![rekognition_sample](https://www.ebia.com.ec/assets/img/products/document_rekognition_sample.png)

The output rekognition has the pdf file of the facial recognition performed as base 64.
* [Rekognition_PDF Demo](https://ebia-documentos-digitales.s3.amazonaws.com/0990633436001/ONE-SHOT/0931427785/309089/EXTRA-DOCUMENT/2023/8/10/EXTRA_DOCUMENT.pdf)

rekognitionError:
``` javascript

```
<a name="demo"></a>
# Demo
* [React.js Demo](https://github.com/EbiaInnovation/ebia-onboarding-SDK-Demo-React)
