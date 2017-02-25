---
title: "setlocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "setlocale_CPP"
  - "vc-pragma.setlocale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Pragma, setlocale"
  - "setlocale pragma"
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# setlocale
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義轉譯寬字元常數和字串常值時使用的地區設定 \(國家\/地區和語言\)。  
  
## 語法  
  
```  
  
#pragma setlocale( "[locale-string]" )  
```  
  
## 備註  
 由於將多位元組字元轉換為寬字元的演算法因地區設定而異，或者編譯和可執行檔將執行的位置可能使用不同的地區設定，因此這個 pragma 提供在編譯時期指定目標地區設定的方法。  這樣可以確保能夠以正確的格式儲存寬字元字串。  
  
 預設的 *locale\-string* 是 ""。  
  
 「C」地區設定會將字串中的每個字元對應其 `wchar_t` 值 \(不帶正負號的短整數\)。  其他可用於 `setlocale` 的值包括[語言字串](../c-runtime-library/language-strings.md)清單中的項目。  例如，您可以發出：  
  
```  
#pragma setlocale("dutch")  
```  
  
 能否發出語言字串取決於電腦的字碼頁和語言 ID 支援。  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)