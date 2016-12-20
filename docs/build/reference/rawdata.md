---
title: "/RAWDATA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rawdata"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RAWDATA dumpbin 選項"
  - "未經處理的資料"
  - "RAWDATA dumpbin 選項"
  - "-RAWDATA dumpbin 選項"
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RAWDATA
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## 備註  
 這個選項會顯示檔案中各個區段的未經處理內容。  引數則控制顯示的格式，如下所示：  
  
|引數|結果|  
|--------|--------|  
|1|預設值。  以十六進位位元組和 ASCII 字元 \(如果具有可列印的表示\) 顯示內容。|  
|2|以十六進位的 2 個位元組值顯示內容。|  
|4|以十六進位的 4 個位元組值顯示內容。|  
|8|以十六進位的 8 個位元組值顯示內容。|  
|NONE|隱藏未經處理的資料 \(Raw Data\)。  這個引數對控制 \/ALL 的輸出相當有用。|  
|*數字*|顯示的行是設定為每行存放 `number` 個值的寬度。|  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 選項可用在以 [\/GL](../../build/reference/gl-whole-program-optimization.md) 編譯器選項所產生的檔案上。  
  
## 請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)