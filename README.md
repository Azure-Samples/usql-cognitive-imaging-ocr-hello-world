---
services: data-lake-analytics
platforms: dotnet
author: saveenr
---

# USQL/Cognitive Imaging OCR Hello World


```
REFERENCE ASSEMBLY ImageCommon;
REFERENCE ASSEMBLY FaceSdk;
REFERENCE ASSEMBLY ImageEmotion;
REFERENCE ASSEMBLY ImageTagging;
REFERENCE ASSEMBLY ImageOcr;

@imgs =
    EXTRACT 
        FileName string, 
        ImgData byte[]
    FROM @"/usqlext/samples/cognition/{FileName}.jpg"
    USING new Cognition.Vision.ImageExtractor();

@ocrs =
    PROCESS @imgs
    PRODUCE FileName,
            Text string
    READONLY FileName
    USING new Cognition.Vision.OcrExtractor();

OUTPUT @ocrs
    TO "/ocr.csv"
    USING Outputters.Csv( outputHeader: true );

```

