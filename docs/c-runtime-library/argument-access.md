---
title: "引數存取 | Microsoft Docs"
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
  - "c.arguments"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "引數存取巨集 [C++]"
  - "可變長度引數清單"
ms.assetid: 7046ae34-a0ec-44f0-815d-3209492a3e19
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 引數存取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示方法呼叫中標記為變數時， `va_arg`、 `va_end`和 `va_start` 巨集提供對函式引數。  這些巨集定義在 ANSI C 相容性的 STDARG.H 和在相容的 VARARGS.H 與 UNIX 系統 v。  
  
### 引數存取巨集  
  
|巨集|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[va\_arg](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|從清單擷取引數|[\<caps:sentence id\="tgt9" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_end](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|重設指標|[\<caps:sentence id\="tgt12" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
|[va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)|將指標為起始點引數清單|[\<caps:sentence id\="tgt15" sentenceid\="f260effcc218d99ea9ab361455fd493c" class\="tgtSentence"\>System::ParamArrayAttribute 類別\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.paramarrayattribute.aspx)|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)