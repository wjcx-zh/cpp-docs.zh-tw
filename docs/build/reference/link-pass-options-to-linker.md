---
title: "/link (傳遞選項給連結器) | Microsoft Docs"
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
  - "/link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/link 編譯器選項 [C++]"
  - "cl.exe 編譯器 [C++], 將選項傳遞至連結器"
  - "link 編譯器選項 [C++]"
  - "-link 編譯器選項 [C++]"
  - "連結器 [C++], 傳遞選項至"
  - "將選項傳遞至連結器"
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /link (傳遞選項給連結器)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳遞一個或多個連結器選項給連結器。  
  
## 語法  
  
```  
/link linkeroptions  
```  
  
## Arguments  
 `linkeroptions`  
 是要傳遞給連結器的連結器選項。  
  
## 備註  
 **\/link** 選項及其連結器選項必須顯示在任何檔名和 CL 選項之後。  在 **\/link** 與 `linkeroptions` 之間需要一個空格。  如需詳細資訊，請參閱[設定連結器選項](../../build/reference/setting-linker-options.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下某一個連結器屬性頁。  
  
4.  修改某一項或多項屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   這個編譯器選項無法以程式設計方式進行變更。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)