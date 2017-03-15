---
title: "DLL 的類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "DLL [C++], MFC"
  - "DLL [C++], 類型"
  - "MFC DLL [C++], 類型"
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# DLL 的類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題將提供幫助您決定要建置 \(Build\) 哪種 DLL 的資訊。  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 可以使用的不同類型 DLL  
 使用 Visual C\+\+，您可以使用 C 或 C\+\+ 建置不使用 Microsoft Foundation Class \(MFC\) 程式庫的 Win32 DLL。  您可使用 Win32 應用程式精靈來建立非 MFC DLL 專案。  
  
 在靜態連結程式庫裡或許多 DLL 裡，MFC 程式庫本身可以與 MFC DLL 精靈一起使用。  如果您的 DLL 是使用 MFC，Visual C\+\+ 便可支援三種不同的 DLL 開發案例：  
  
-   建置會靜態連結至 MFC 的標準 DLL  
  
-   建置會動態連結至 MFC 的標準 DLL  
  
-   建置 MFC 擴充 DLL，此 DLL 永遠會動態連結至 MFC  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL：概觀](../build/extension-dlls-overview.md)  
  
-   [要使用哪一種 DLL](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> 決定要使用哪一種 DLL  
 如果您的 DLL 不使用 MFC，請使用 Visual C\+\+ 建置非 MFC Win32 DLL。  將您的 DLL 連結至 MFC \(靜態或動態\) 會使用相當多的磁碟空間和記憶體。  除非您的 DLL 真的會使用到 MFC，否則您不應該連結至 MFC。  
  
 如果您的 DLL 會使用 MFC，而且會由 MFC 或非 MFC 應用程式所使用，則您必須建置動態連結至 MFC 的標準 DLL 或是靜態連結至 MFC 的標準 DLL。  在大多數的情況下，您會想要使用動態連結至 MFC 的標準 DLL，因為 DLL 的檔案大小會小很多，而且使用 MFC 的共用版本可節省許多的記憶體。  如果是靜態地連結至 MFC，因為 DLL 會載入自己的 MFC 程式庫碼私用 \(Private\) 複本，所以其大小會大得多，而且可能會佔用額外的記憶體。  
  
 因為動態連結不需要連結 MFC 本身，所以建置動態連結至 MFC 的 DLL 比建置靜態連結至 MFC 的 DLL 迅速。  在偵錯版中的連結器必須壓縮偵錯資訊，更可說明這點。  由於連結已經包含偵錯資訊的 DLL，因此您的 DLL 內只有較少的偵錯訊息需要壓縮。  
  
 動態連結至 MFC 的一個缺點是，您必須將共用的 DLL Mfcx0.dll 和 Msvcrxx.dll \(或類似的檔案\) 與您的 DLL 一起散佈。  MFC DLL 可以自由重新散佈，但是您仍然必須在安裝程式裡安裝 DLL。  除此之外，您還必須送出 Msvcrxx.dll，它包含您的程式和 MFC DLL 本身會使用的 C 執行階段程式庫。  
  
 如果您的 DLL 只供 MFC 可執行檔使用，您可以選擇建置標準 DLL 或擴充 DLL。  如果您的 DLL 實作衍生自現有 MFC 類別的可重複使用類別，或者您需要在應用程式和 DLL 之間傳遞從 MFC 衍生的物件，則必須建置擴充 DLL。  
  
 如果您的 DLL 動態連結至 MFC，則可能需要與您的 DLL 一起轉散發 MFC DLL。  當共用多個可執行檔間的類別庫 \(Class Library\) 以節省磁碟空間和降低使用記憶體時，這種架構特別有用。  
  
 版本 4.0 之前的 Visual C\+\+ 只支援兩種使用 MFC 的 DLL 類型：USRDLL 和 AFXDLL。  靜態連結至 MFC 的標準 DLL 與之前的 USRDLL 有相同的特性。  MFC 擴充 DLL 與之前的 AFXDLL 有相同的特性。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [非 MFC DLL：概觀](../build/non-mfc-dlls-overview.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [擴充 DLL：概觀](../build/extension-dlls-overview.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)