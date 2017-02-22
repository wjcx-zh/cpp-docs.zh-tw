---
title: "以程式設計方式列印 | Microsoft Docs"
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
  - "主動式文件 [C++], 列印"
  - "IPrint 介面"
  - "列印 [MFC]"
  - "列印 [MFC], 主動式文件"
  - "列印 [MFC], 程式設計"
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 以程式設計方式列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 提供方法來唯一識別保存文件 \(**GetClassFile**\) 並載入至其關聯的程式碼 \(`CoCreateInstance`、**QueryInterface\(IID\_IPersistFile\)**、**QueryInterface\(IID\_IPersistStorage\)**、**IPersistFile::Load** 和 **IPersistStorage::Load**\)。  若要進一步啟用列印文件，主動式文件內含項目 \(使用現有的 OLE 設計，一開始並不隨附 OLE 2.0\) 會引入基底標準列印介面 `IPrint`，通常可透過可以載入文件類型的持續性狀態的物件取得。  每個現用文件的檢視可以選擇性地支援 **IPrint**  介面，以提供這些功能。  
  
 `IPrint` 介面定義如下：  
  
 `interface IPrint : IUnknown`  
  
 `{`  
  
 `HRESULT SetInitialPageNum([in] LONG nFirstPage);`  
  
 `HRESULT GetPageInfo(`  
  
 `[out] LONG *pnFirstPage,`  
  
 `[out] LONG *pcPages);`  
  
 `HRESULT Print(`  
  
 `[in] DWORD grfFlags,`  
  
 `[in,out] DVTARGETDEVICE **pptd,`  
  
 `[in,out] PAGESET ** ppPageSet,`  
  
 `[in,out] STGMEDIUM **ppstgmOptions,`  
  
 `[in] IContinueCallback* pCallback,`  
  
 `[in] LONG nFirstPage,`  
  
 `[out] LONG *pcPagesPrinted,`  
  
 `[out] LONG *pnPageLast);`  
  
 `};`  
  
 用戶端和容器使用 **IPrint::Print** 指定列印控制項旗標、目標裝置、列印的頁面以及其他選項，指示文件在載入時列印。  用戶端也可以透過 `IContinueCallback` 介面控制列印的後續 \(參看下方\)。  
  
 此外， **IPrint::SetInitialPageNum** 透過連續的為頁面編號，支援列印一系列的資料，為類似 Office 文件夾的現用文件容器的優點。  **IPrint::GetPageInfo** 允許呼叫端可以擷取先前傳遞至 **SetInitialPageNum** \(或文件的內部預設啟動頁碼\) 的起始頁碼以及文件的頁面數目，使顯示分頁資訊更簡單。  
  
 支援 `IPrint` 的物件以儲存在物件的 CLSID 下的「可列印」索引鍵標記：  
  
 HKEY\_CLASSES\_ROOT\\CLSID\\{...}\\Printable  
  
 `IPrint` 通常實作在支援 `IPersistFile` 或 `IPersistStorage` 的相同物件上。  呼叫端可查看「可列印」索引鍵的註冊，注意以程式設計方式列印一些類別保存狀態的功能。  目前，「可列印」表示至少支援 `IPrint`；其他介面會在未來定義並可以透過 `QueryInterface` \(**IPrint**  表示基礎支援層級\) 取得。  
  
 在列印程序期間，您可能想要初始化列印控制項的用戶端或容器控制是否應該繼續列印。  例如，容器可能支援應該儘快終止列印工作的「停止列印」命令。  若要支援這項功能，可列印物件的用戶端可以介面 `IContinueCallback` 實作小型通知接收物件：  
  
 `interface IContinueCallback : IUnknown`  
  
 `{`  
  
 `HRESULT FContinue(void);`  
  
 `HRESULT FContinuePrinting(`  
  
 `[in] LONG cPagesPrinted,`  
  
 `[in] LONG nCurrentPage,`  
  
 `[in] LPOLESTR pszPrintStatus);`  
  
 `};`  
  
 這個介面做為替代 Win32 API 中各種繼續程式 \(例如列印的 **AbortProc** 和中繼檔列舉的 **EnumMetafileProc** \) 的泛型繼續回呼函式十分有用。  因此這個介面設計適用於各種費時的程序。  
  
 在最常見的案例，**IContinueCallback::FContinue** 函式是由任何費時的流程定期呼叫。  接收物件傳回 `S_OK` 以繼續作業，並傳回 **S\_FALSE** 盡快停止程式。  
  
 不過，**FContinue** 不會用在 **IPrint::Print** 中；相反地，會使用 **IContinueCallback::FContinuePrint**。  所有列印物件應該定期呼叫 **FContinuePrinting**， 傳遞已列印的頁面數目、正在列印的網頁數目，另外傳遞一個字串描述用戶端可以選擇顯示給使用者的列印狀態 \(例如「19 頁中的第 5 頁」\)。  
  
## 請參閱  
 [主動式文件容器](../mfc/active-document-containers.md)