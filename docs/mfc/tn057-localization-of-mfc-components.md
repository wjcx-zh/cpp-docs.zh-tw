---
title: "TN057：MFC 元件的當地語系化 | Microsoft Docs"
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
  - "vc.mfc.components"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "元件 [MFC], 當地語系化"
  - "DLL [C++], 當地語系化 MFC"
  - "當地語系化 [C++], MFC 元件"
  - "當地語系化 [C++], MFC 資源"
  - "當地語系化 [C++], 資源"
  - "MFC DLL [C++], 當地語系化"
  - "資源 [MFC], 當地語系化"
  - "TN057"
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN057：MFC 元件的當地語系化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個會描述一些您可以使用當地語系化元件的設計和程序，因此，如果應用程式或 OLE automation 控制項或使用 MFC 的 DLL。  
  
## 概觀  
 具有真正地解析的兩個問題，在當地語系化 MFC 使用的元件。  首先，您必須當地語系化您的資源—字串、對話方塊和專屬於您元件的其他資源。  使用 MFC 建置的大部分元件也包括並使用由 MFC 定義的資源。  您必須提供當地語系化 MFC 資源。  所幸， MFC 已經提供數種語言。  
  
 此外，在其目標環境應該準備您的元件執行 \(歐洲個人或 DBCS 讓環境\)。  在大部分的情況下，這取決於您的會將字元與高位元正確設定和管理與雙位元組字元的應用程式資料。  MFC 時，根據預設，這兩個環境，這類具有參數的不同資源的所有平台用於設定時間的單一全球二進位檔是可能的。  
  
## 當地語系化元件的資源  
 當地語系化您的應用程式或 DLL 應該包含取代資源與目標語言的資源。  對於您自己的資源，這是相當簡單的:若要在資源編輯器的資源並建置應用程式。  如果您的程式碼正確撰寫沒有字串或文字要當地語系化硬式編碼在 C\+\+ 原始程式碼中的–所有當地語系化可修改資源已完成。  實際上，您可以實作自己的元件這類所有提供當地語系化版本也不包含原始程式碼的組建。  這是更複雜的，不過，很值並是 MFC 選取的機制。  藉由直接載入 EXE 或 DLL 檔中的資源編輯器和編輯資源當地語系化應用程式也可以。  在可能時，它需要這些變更的 reapplication，每次建置應用程式的新版本。  
  
 是找出所有資源個別的 DLL 的一種方式避免，有時稱為附屬 DLL。  這個 DLL 動態地載入執行階段中，而資源從該 DLL 載入而不是從主要模組的所有程式碼。  MFC 直接支援這個方法。  考慮當應用程式呼叫 MYAPP.EXE;它可能有位於 DLL 呼叫的 MYRES.DLL 其所有的資源。  在應用程式的 `InitInstance` 將執行下列載入該 DLL 和 MFC 會從該位置載入資源:  
  
```  
CMyApp::InitInstance()  
{  
   // one of the first things in the init code  
   HINSTANCE hInst = LoadLibrary("myres.dll");  
   if (hInst != NULL)  
      AfxSetResourceHandle(hInst);  
  
   // other initialization code would follow  
   .  
   .  
   .  
}  
```  
  
 從該時間點之後，從 MFC DLL 會載入資源而不是從 myapp.exe。  所有資源，不過，必須存在於該 DLL;MFC 不會搜尋應用程式執行個體尋找特定資源。  這個技術同樣地套用至標準 DLL 以及 OLE automation 控制項。  您的安裝程式將複製資源地區設定使用者會想要 MYRES.DLL 的正確版本。  
  
 建立僅含資源的 DLL 是相當容易的。  您建立 DLL 專案，將 .RC 檔到它，並將需要的資源。  如果您未使用這個技巧的現有專案，您可以從該專案的資源。  將資源檔加入至專案之後，您幾乎可以建立專案。  您必須做的事設定連結器選項包括 **\/NOENTRY**。  這會告訴連結器 DLL 沒有進入點\)，因為它沒有程式碼，所以它沒有進入點。  
  
> [!NOTE]
>  在 Visual C\+\+ 4.0 的資源編輯器和更新每個 .RC 的多種語言檔案。  這可讓非常容易管理在單一專案的當地語系化。  每種語言的資源是由資源編輯器產生的前置處理器指示詞的控制項。  
  
## 使用提供的 MFC 當地語系化資源  
 您建立重複使用從 MFC 兩件事的任何 MFC 應用程式:程式碼和資源。  即 MFC 具有各種錯誤訊息、內建對話方塊和 MFC 類別使用的其他資源。  為了完全當地語系化您的應用程式，您不僅需要當地語系化您的應用程式中的資源，而且，直接取自 MFC 的資源。  MFC 會自動提供許多不同語言的資源檔，，因此，如果您以為目標的語言已經是其中一個語言 MFC 支援，您需要判斷您使用這些當地語系化資源。  
  
 在撰寫本文時， MFC 支援中文、德文、西班牙文、法文、義大利文、日文和韓文。  包含這些當地語系化版本的檔案在 MFC \\ Include \\ L.\* \(「L」代表當地語系化\) 目錄。  例如德文檔案在 MFC \\ Include \\ L.DEU，。  若要讓您的應用程式使用這些 RC 檔而不是位於 MFC 的檔案\\ include，請將 `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` 加入至您的 RC 命令列 \(這是範例;您會需要替代安裝 Visual C\+\+\) 選項以及目錄的地區設定。  
  
 上述表示，如果您的應用程式連結靜態與 MFC 一起使用。  大部分的應用程式連結動態 \(因為這是 AppWizard 預設值\)。  在這個案例中，而不僅是程式碼動態連接\)，因此是資源。  因此，您可以當地語系化您的應用程式中的資源，不過， MFC 實作資源會從載入 MFC7x.DLL \(或更新版本\) 或從 MFC7xLOC.DLL，如果有的話。  您可以存取此從兩個不同的角度。  
  
 這種更複雜的方法將傳輸的當地語系化 MFC7xLOC.DLLs \(例如 MFC7xDEU，德文、MFC7xESP.DLL 西班牙文的等\)，或更新版本，以及安裝適當的 MFC7xLOC.DLL 輸入系統目錄，當使用者安裝應用程式時。  這可以是非常複雜的開發人員，且為這類不建議使用者。  請參閱 [Technical Note 56](../mfc/tn056-installation-of-localized-mfc-components.md) 。如需此技術及其警告的詳細資訊。  
  
 這種最簡單、最安全的方法是將當地語系化 MFC 資源在應用程式或 DLL \(或其附屬 DLL，如果您使用\)。  這可避免適當安裝 MFC7xLOC.DLL 的問題。  若要這麼做，請按照指定的靜態情況的相同指示以上 \(適當地設定 RC 命令列要當地語系化資源的點\)，不過，您也必須移除由 AppWizard 增加的 `/D_AFXDLL` 定義。  當 `/D_AFXDLL` 被定義時， AFXRES.H \(和其他 MFC RC 檔\) 實際上不會定義任何資源 \(因為從 MFC DLL 提取\)。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)