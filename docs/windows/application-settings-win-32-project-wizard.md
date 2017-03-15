---
title: "Win 32 應用程式精靈、應用程式設定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.win32.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式設定 [C++]"
  - "Win32 專案精靈, 應用程式設定"
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Win 32 應用程式精靈、應用程式設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個精靈頁面來設定 Win32 專案的選項。  
  
 **應用程式類型**  
 建立指定的應用程式類型。  
  
|選項|說明|  
|--------|--------|  
|**主控台應用程式**|建立主控台應用程式 \(Console Application\)。  主控台程式是以[主控台函式](https://msdn.microsoft.com/en-us/library/ms813137.aspx)開發的，這些函式能在主控台視窗中提供字元模式支援。  Visual C\+\+ [執行階段程式庫](../c-runtime-library/c-run-time-library-reference.md) 提供標準 I\/O 函式 \(例如 **printf\_s\(\)** 和 **scanf\_s\(\)**\) 透過主控台視窗進行輸出和輸入。  主控台應用程式並不具圖形使用者介面 \(Graphic User Interface，GUI\)。  它會編譯為 .exe 檔，然後像獨立 \(Stand\-Alone\) 應用程式一樣從命令列來執行它。<br /><br /> 您可將 MFC 和 ATL 支援加入至主控台應用程式。|  
|**Windows 應用程式**|建立 Win32 程式。  Win32 程式是使用 C 或 C\+\+ 寫入的可執行應用程式 \(EXE\)，利用呼叫 Win32 API 來建立圖形使用者介面。<br /><br /> 您無法將 MFC 或 ATL 支援加入至 Windows 應用程式中。|  
|**DLL**|建立 Win32 動態連結程式庫 \(DLL\)。  Win32 DLL 是使用 C 或 C\+\+ 寫入的二進位檔案 \(Binary File\)，利用呼叫 Win32 API 而非 MFC 類別，同時也可當做函式的共用程式庫以讓多個應用程式同時使用。<br /><br /> 您無法將 MFC 或 ATL 支援加入至 DLL 應用程式中。  您可指出 DLL 匯出符號。|  
|**靜態程式庫**|建立靜態程式庫。  靜態程式庫是一種檔案，其中包含物件和其函式以及當建置 \(Build\) 可執行檔時連結至程式的資料。  此主題將說明如何為靜態程式庫建立起始檔案 \(Starter File\) 和[專案屬性](../ide/property-pages-visual-cpp.md)。  靜態程式庫檔案提供下列好處：<br /><br /> -   如果使用的應用程式呼叫 Win32 API，而不是 MFC 類別，則 Win32 靜態程式庫會相當有用。<br />-   無論 Windows 應用程式的其他部分是否以 C 或 C\+\+ 撰寫，連結的過程都是一樣的。<br />-   可將靜態程式庫連結至 MFC 架構程式或是非 MFC 程式。|  
  
 **其他選項**  
 依照應用程式類型來定義其支援和選項。  
  
|選項|說明|  
|--------|--------|  
|**空專案**|指定專案檔為空白。  如果您有一組原始程式碼檔 \(例如 .cpp 檔、標頭檔、圖示、工具列、對話方塊等等\) 並且要在 Visual C\+\+ 開發環境中建立專案，您必須先建立空白專案，接著將檔案加入至專案。<br /><br /> 靜態程式庫專案無法使用這個選項。|  
|**匯出符號**|指定 DLL 專案匯出符號。|  
|**先行編譯標頭**|指定靜態程式庫專案使用先行編譯標頭。|  
|核對安全開發週期 \(SDL\)|如需 SDL 的詳細資訊，請參閱 [Microsoft Security Development Lifecycle \(SDL\)  Process Guidance](84aed186-1d75-4366-8e61-8d258746bopq)。|  
  
 **加入支援：**  
 加入對 Visual C\+\+ 提供之程式庫的支援。  
  
|選項|說明|  
|--------|--------|  
|**ATL**|建置為支援 Active Template Library \(ATL\) 中之類別的專案。  僅限 Win32 主控台應用程式。<br /><br /> **注意**：這個選項並不指示使用 ATL 程式碼精靈加入 ATL 物件的支援。  您只能將 ATL 物件加入至具有 ATL 支援的 ATL 專案或 MFC 專案。|  
|**MFC**|建置為支援 MFC 程式庫的專案。  僅限 Win32 主控台應用程式和靜態程式庫。|  
  
## 請參閱  
 [Win32 應用程式精靈](../windows/win32-application-wizard.md)   
 [如何：建立 Windows 傳統型應用程式](../Topic/How%20to:%20Create%20a%20Windows%20Desktop%20Application.md)