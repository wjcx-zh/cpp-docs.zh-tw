---
title: 以程式設計方式列印 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbbc9792fcaec6713e13b4665568017bc5ce1bdc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930923"
---
# <a name="programmatic-printing"></a>以程式設計方式列印
OLE 提供方法來唯一識別持續性文件 (`GetClassFile`) 並將它們載入至其相關聯的程式碼 (`CoCreateInstance`， `QueryInterface(IID_IPersistFile)`， `QueryInterface(IID_IPersistStorage)`， `IPersistFile::Load`，和`IPersistStorage::Load`)。 為了要進一步啟用列印文件，使用中文件內含項目 (使用現有的 OLE 設計，一開始並未隨附於 OLE 2.0) 會引入基底標準列印介面 `IPrint`，通常可透過可以載入文件類型的持續性狀態的物件取得。 主動式文件的每個檢視可以選擇性地支援`IPrint`介面，以提供這些功能。  
  
 `IPrint` 介面定義如下：  
  
```  
interface IPrint : IUnknown  
    {  
    HRESULT SetInitialPageNum([in] LONG nFirstPage);  
    HRESULT GetPageInfo(  
        [out] LONG *pnFirstPage,  
        [out] LONG *pcPages);  
    HRESULT Print(  
        [in] DWORD grfFlags,  
        [in,out] DVTARGETDEVICE **pptd,  
        [in,out] PAGESET ** ppPageSet,  
        [in,out] STGMEDIUM **ppstgmOptions,  
        [in] IContinueCallback* pCallback,  
        [in] LONG nFirstPage,  
        [out] LONG *pcPagesPrinted,  
        [out] LONG *pnPageLast);  
    };  
```  
  
 用戶端和容器只使用`IPrint::Print`指示文件，該文件載入後，指定列印控制項旗標、 目標裝置、 要列印的頁面時列印本身和其他選項。 用戶端也可以透過 `IContinueCallback` 介面控制列印的接續工作 (請參閱下方)。  
  
 此外，`IPrint::SetInitialPageNum`支援的功能來列印文件的一系列一個編號頁面順暢，顯然類似 Office Binder 的現用文件容器的好處。 `IPrint::GetPageInfo` 使顯示分頁資訊簡單允許呼叫端擷取的起始頁碼先前傳遞至`SetInitialPageNum`（或文件的內部預設啟動頁碼） 和文件中的頁數。  
  
 支援 `IPrint` 的物件在登錄中儲存物件的 CLSID 下以「Printable」機碼加以標記：  
  
 HKEY_CLASSES_ROOT\CLSID\\{...}\Printable  
  
 `IPrint` 通常會在支援 `IPersistFile` 或 `IPersistStorage` 的相同物件上實作。 呼叫端可在登錄中查看「Printable」機碼，以記錄以程式設計方式列印一些類別保存狀態的功能。 目前，「 可列印 」 表示支援至少`IPrint`; 其他介面可定義在未來的會是可透過`QueryInterface`其中`IPrint`只代表基本層級的支援。  
  
 在列印程序進行期間，您可能想要初始化列印控制項的用戶端或容器控制是否應該繼續列印。 例如，容器可能支援應該儘快終止列印工作的「停止列印」命令。 若要支援這項功能，可列印物件的用戶端可以實作具有 `IContinueCallback` 介面的小型通知接收物件：  
  
```  
interface IContinueCallback : IUnknown  
    {  
    HRESULT FContinue(void);  
    HRESULT FContinuePrinting(  
        [in] LONG cPagesPrinted,  
        [in] LONG nCurrentPage,  
        [in] LPOLESTR pszPrintStatus);  
    };  
```  
  
 這個介面設計為取代的 Win32 API 中各種接續程序的泛型接續回呼函式很有用 (例如`AbortProc`列印和`EnumMetafileProc`中繼檔列舉)。 因此這個介面設計適用於各種費時的程序。  
  
 在大部分的泛型的情況下，`IContinueCallback::FContinue`函式由任何耗時的處理序定期呼叫。 接收物件會傳回 S_OK 來繼續作業，並儘速停止程序 S_FALSE。  
  
 `FContinue`不過，不是內容中`IPrint::Print`; 相反地，列印使用`IContinueCallback::FContinuePrint`。 列印中的物件應該定期呼叫`FContinuePrinting`傳遞已列印的頁面數目、 正在列印的頁面數目和描述用戶端可以選擇顯示給使用者 （例如 「 頁列印狀態的其他字串5 的 19")。  
  
## <a name="see-also"></a>另請參閱  
 [主動式文件容器](../mfc/active-document-containers.md)

