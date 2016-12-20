---
title: "編譯器錯誤 C2011 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2011"
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': 'type' 類型重複定義  
  
 識別項已定義為 `type`。  檢查識別項是否重複定義。  
  
 如果您將標頭檔或類型庫多次匯入至相同檔案中，您也會收到 C2011。  若要避免多次包含標頭檔中定義的類型，請在標頭檔中使用 include 防護或 `#pragma` [once](../../preprocessor/once.md) 指示詞。  
  
 如果您需要尋找重複定義的類型的初始宣告，您可以使用 [\/P](../../build/reference/p-preprocess-to-a-file.md) 編譯器旗標，產生前置處理過的輸出來傳遞至編譯器。  您可以使用文字搜尋工具，在輸出檔中尋找重複定義的識別項的執行個體。  
  
 下列範例會產生 C2011，並示範修正此問題的方法：  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```