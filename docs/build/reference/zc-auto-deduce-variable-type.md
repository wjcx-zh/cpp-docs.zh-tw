---
title: "/Zc:auto (推算變數類型) | Microsoft Docs"
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
  - "/Zc:auto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 (C++)"
  - "推算變數類型 (C++)"
  - "Zc 編譯器選項 (C++)"
  - "-Zc 編譯器選項 (C++)"
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:auto (推算變數類型)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/Zc:auto\[\-\]** 編譯器選項會告知編譯器如何使用 [auto 關鍵字](../../cpp/auto-keyword.md)，來宣告變數。  如果您指定預設選項 **\/Zc:auto**，則編譯器會從其初始化運算式，來推斷所宣告變數的類型。  如果您指定  **\/Zc:auto\-**，則編譯器會將變數配置為自動儲存類別。  
  
## 語法  
  
```  
/Zc:auto[-]  
```  
  
## 備註  
 C\+\+ 標準為 `auto` 關鍵字定義了原始和修訂的意義。  在 [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)] 以前，該關鍵字會在自動儲存類別中宣告變數，也就是具有區域存留期的變數。  從 [!INCLUDE[cpp_dev10_long](../../build/includes/cpp_dev10_long_md.md)] 開始，該關鍵字會從宣告的初始化運算式，推斷變數的類型。使用 **\/Zc:auto\[\-\]** 編譯器選項，可以告知編譯器，使用 `auto` 關鍵字的原始或修訂的意義。  
  
 如果 `auto` 關鍵字的使用與目前編譯器選項衝突，則編譯器會發出適當的診斷訊息。  如需詳細資訊，請參閱[auto 關鍵字](../../cpp/auto-keyword.md)。  如需 Visual C\+\+ 一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[組態屬性\] 節點。  
  
3.  按一下 \[C\/C\+\+\] 節點。  
  
4.  按一下 \[命令列\] 節點。  
  
5.  新增 **\/Zc:auto** 或 **\/Zc:auto\-** 至 \[其他選項\] 窗格。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)   
 [auto 關鍵字](../../cpp/auto-keyword.md)