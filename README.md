# IBMWatsonLanguageTranslator Package

* Domain: https://www.ibm.com/watson
* Credentials: username, password

## How to get credentials: 
0. Register to [IBM Bluemix Console](https://console.ng.bluemix.net/registration/) 
1. After log in choose Natural Language Classifier from [services](https://console.ng.bluemix.net/catalog/?category=watson)
2. Connect Natural Language Classifier to your application at the left side, choose pricing plan and click on 'Create' button at the bottom of the page.
3. Click on 'Service Credentials' tab to see your username and password.
## IBMWatsonLanguageTranslator.translate
Translates input text from the source language to the target language.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.
| modelId     | String     | The unique model_id of the translation model used to translate text. The model_id inherently specifies source, target language, and domain. If the model_id is specified, there is no need for the source and target parameters, and the values will be ignored.
| source      | String     | Used in combination with target as an alternative way to select the model for translation. When target and source are set, and model_id is not set, the system choose a default model with the right language pair to translate (usually the model based on the news domain).
| target      | String     | Translation target language in 2 or 5 letter language code. Should use 2 letter codes except for when clarifying between multiple supported languages. When model_id is used directly, it will override the source-target language combination. Also, when a 2 letter language code is used, and no suitable default is found (such as “zh”), it returns an error.
| text        | String     | Input text in UTF-8 encoding. Multiple text query parameters indicate multiple input paragraphs, and a single string is valid input.

## IBMWatsonLanguageTranslator.getIdentifiableLanguages 
Return the list of languages it can detect.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.

## IBMWatsonLanguageTranslator.identifyLanguage 
Identify the language in which a text is written.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.
| text        | String     | Input text in UTF-8 format.

## IBMWatsonLanguageTranslator. getModels
Lists available models for the Language translator service with option to filter by source or by target language.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.
| default     | Boolean    | Valid values are leaving it unset, 'true' and 'false'. When 'true', it filters models to return the default model or models. When 'false' it returns the non-default model or models. If not set, all models (default and non-default) return.
| source      | String     | Define with target. Filters models by source language.
| target      | String     | Define with source. Filters models by target language.

## IBMWatsonLanguageTranslator.createModel
Uploads a TMX glossary file on top of a domain to customize a translation model.Depending on the size of the file, training can range from minutes for a glossary to several hours for a large parallel corpus. Glossary files must be less than 10 MB. The cumulative file size of all uploaded glossary and corpus files is limited to 250 MB.

| Field            | Type       | Description
|------------------|------------|----------
| username         | credentials| Username obtained from IBM Bluemix.
| password         | credentials| Password obtained from IBM Bluemix.
| baseModelId      | String     | Specifies the domain model that is used as the base for the training. To see current supported domain models, use `getModels` method.
| name             | String     | The model name. Valid characters are letters, numbers, -, and _. No spaces.
| forcedGlossary   | File       | A TMX file with your customizations. Anything that is specified in this file completely overwrites the domain data translation. You can upload only one glossary with a file size less than 10 MB per call.
| parallelCorpus   | File       | A TMX file that contains entries that are treated as a parallel corpus instead of a glossary.
| monolingualCorpus| File       | A UTF-8 encoded plain text file that is used to customize the target language model.

## IBMWatsonLanguageTranslator.deleteModel
Deletes trained translation models.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.
| modelId     | String     | The model identifier.

## IBMWatsonLanguageTranslator.getModelDetails
Returns information, including training status, about a specified translation model.

| Field       | Type       | Description
|-------------|------------|----------
| username    | credentials| Username obtained from IBM Bluemix.
| password    | credentials| Password obtained from IBM Bluemix.
| modelId     | String     | The model identifier.

