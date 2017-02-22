---
title: "使用 DLL 的優點 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], 優點"
  - "動態連結 [C++]"
  - "動態載入連結 [C++]"
  - "連結 [C++], 動態和靜態的比較"
  - "連結 [C++], 動態和靜態的比較"
ms.assetid: 8956c8ee-e7b3-446f-a0c6-462381747690
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用 DLL 的優點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

動態連結有下列優點：  
  
-   節省記憶體和降低交換。  許多處理序可以同時使用單一 DLL 來共用記憶體裡 DLL 的單一複本。  相反地，Windows 必須為每個使用靜態連結程式庫所建置的應用程式，將程式庫碼的複本載入記憶體。  
  
-   節省磁碟空間。  許多應用程式可以共用磁碟上的單一 DLL 複本。  相反地，每一個使用靜態連結程式庫建置的應用程式，會將程式庫碼以不同的複本連結至其可執行檔映像。  
  
-   升級對於 DLL 而言較為容易。  當 DLL 的函式變更時，只要函式的引數和傳回值沒有改變，使用這些函式的應用程式就不需要重新編譯或重新連結。  相反地，當函式變更時，靜態連結目的碼 \(Object Code\) 便需要重新連結應用程式。  
  
-   提供售後支援。  例如，顯示卡驅動程式 DLL 可以修改，以便支援應用程式推出時尚無的顯示卡。  
  
-   支援多種語言程式。  只要程式遵循函式的呼叫慣例，以不同程式設計語言撰寫的程式就可以呼叫相同的 DLL 函式。  程式和 DLL 函式在下列條件中必須是相容的：函式預期的引數被放入堆疊的順序、函式或應用程式是否負責清除堆疊，以及任何引數是否傳入暫存器。  
  
-   提供擴充 MFC 程式庫類別的機制。  您可以由現有的 MFC 類別衍生類別，並且將它們放在 MFC 擴充 DLL 以便 MFC 應用程式使用。  
  
-   簡化國際版本的建立。  在 DLL 裡放置資源會使建立應用程式的國際版本變得更容易。  您可以將應用程式每種語言版本的字串放在不同的資源 DLL 中，並且讓不同語言的版本載入適當的資源。  
  
 使用 DLL 可能的缺點是，應用程式不是獨立的 \(Self\-Contained\)；它必須依賴不同 DLL 模組的存在。  
  
## 您想要執行甚麼工作？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [初始化 DLL](../build/initializing-a-dll.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL：概觀](../build/extension-dlls-overview.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)