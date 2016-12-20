---
title: "如何：將 Visual C++ 專案設定成以 64 位元平台為目標 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "平台 [C++], 64 位元"
  - "64 位元程式設計 [C++], 設定專案"
  - "專案組態 [C++]"
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：將 Visual C++ 專案設定成以 64 位元平台為目標
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 Visual Studio 的專案組態設定 C\+\+ 應用程式，鎖定 64 位元平台。 您也可以將 Win32 專案設定移轉至 64 位元專案組態。  
  
### 設定 C\+\+ 應用程式鎖定 64 位元平台  
  
1.  請開啟您想要設定的 C\+\+ 專案。  
  
2.  開啟該專案的屬性頁面。 如需詳細資訊，請參閱[如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  
  
    > [!NOTE]
    >  若為 .NET 專案，請確定在 \[\<專案名稱\> 屬性頁\] 對話方塊中選取了 \[組態屬性\] 節點或其子節點之一；否則，\[組態管理員\] 按鈕將仍然無法使用。  
  
3.  選擇 \[組態管理員\] 按鈕開啟 \[組態管理員\] 對話方塊。  
  
4.  在 \[使用中的方案平台\] 下拉式清單中，選取 \[\<新增...\>\] 選項開啟 \[新增方案平台\] 對話方塊。  
  
5.  在 \[輸入或選擇新平台\] 下拉式清單中選取 64 位元平台。  
  
    > [!NOTE]
    >  在 \[新增方案平台\] 對話方塊中，您可以使用 \[複製設定值來源\] 選項將現有的專案設定複製到新的 64 位元專案組態。  
  
6.  選擇 \[**確定**\] 按鈕。 上個步驟所選取的平台會出現在 \[組態管理員\] 對話方塊的 \[使用中的方案平台\] 之下。  
  
7.  選擇 \[組態管理員\] 對話方塊的 \[關閉\] 按鈕，然後選擇 \[\<專案名稱\> 屬性頁\] 對話方塊的 \[確定\] 按鈕。  
  
### 將 Win32 專案設定複製到 64 位元專案組態  
  
-   當 \[新增方案平台\] 對話方塊在您設定專案鎖定 64 位元平台時開啟，請在 \[複製設定值來源\] 下拉式清單中選取 \[Win32\]。 這些專案設定會自動在專案層級上更新：  
  
    -   [\/MACHINE](../build/reference/machine-specify-target-platform.md) 連結器選項會設為 **\/MACHINE:X64**。  
  
    -   \[登錄輸出\] 已關閉。 如需詳細資訊，請參閱[連結器屬性頁](../ide/linker-property-pages.md)。  
  
    -   \[目標環境\] 設為 **\/env x64**。 如需詳細資訊，請參閱[MIDL 屬性頁：一般](../ide/midl-property-pages-general.md)。  
  
    -   \[驗證參數\] 已清除並重設為預設值。 如需詳細資訊，請參閱[MIDL 屬性頁：進階](../ide/midl-property-pages-advanced.md)。  
  
    -   如果 \[偵錯資訊格式\] 在 Win32 專案組態中設為 **\/ZI**，則在 64 位元專案組態中就會設為 **\/Zi**。 如需詳細資訊，請參閱[\/Z7、\/Zi、\/ZI \(偵錯資訊格式\)](../build/reference/z7-zi-zi-debug-information-format.md)。  
  
    > [!NOTE]
    >  如果它們在檔案層級上覆寫，這些專案屬性全都不會變更。  
  
## 請參閱  
 [64 位元應用程式](../Topic/64-bit%20Applications.md)   
 [為 64 位元設定程式](../build/configuring-programs-for-64-bit-visual-cpp.md)   
 [偵錯 64 位元應用程式](../Topic/Debug%2064-Bit%20Applications.md)