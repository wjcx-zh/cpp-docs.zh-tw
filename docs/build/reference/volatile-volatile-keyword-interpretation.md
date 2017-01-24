---
title: "/volatile (volatile 關鍵字轉譯) | Microsoft Docs"
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
  - "/volatile:iso"
  - "/volatile:ms"
  - "/volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/volatile 編譯器選項"
  - "/volatile 編譯器選項 [C++]"
  - "volatile 編譯器選項"
  - "-volatile 編譯器選項"
  - "volatile 編譯器選項 [C++]"
  - "-volatile 編譯器選項 [C++]"
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /volatile (volatile 關鍵字轉譯)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定解譯 [volatile](../../cpp/volatile-cpp.md) 關鍵字的方式。  
  
## 語法  
  
```  
/volatile:{iso|ms}  
```  
  
## Arguments  
 **\/volatile:iso**  
 選取 ISO 標準 C\+\+ 語言所定義的嚴格 `volatile` 語意。  暫時性存取時不保證 Acquire\/release 語意。  如果編譯器以 ARM 為目標，這是 `volatile` 的預設解譯。  
  
 **\/volatile:ms**  
 選取 Microsoft 擴充的 `volatile` 語意，這可超越 ISO 標準 C\+\+ 語言來提高記憶體順序保證。  暫時性存取時保證 Acquire\/release 語意。  不過，這個選項也會強制編譯器產生硬體記憶體屏障，可能會在 ARM 和其他弱式記憶體順序架構上增加重大額外負荷。  如果編譯器以除了 ARM 以外的任何其他平台為目標，這是 `volatile` 的預設解譯。  
  
## 備註  
 當您處理跨執行緒共用的記憶體時，強烈建議您搭配明確的同步處理原始物件和編譯器內建來使用 **\/volatile:iso**。  如需詳細資訊，請參閱[volatile](../../cpp/volatile-cpp.md)。  
  
 如果您在專案中移植現有的程式碼或變更這個選項，啟用警告 [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) 識別受語意差異影響的程式碼位置，可能會很有用。  
  
 沒有控制這個選項的 `#pragma` 對應項。  
  
### 若要在 Visual Studio 中設定 \/volatile 編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項。**\] 方塊中，加入 `/volatile:iso` 或 `/volatile:ms`。  
  
## 請參閱  
 [volatile](../../cpp/volatile-cpp.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)