---
title: 傳遞 OLE DB 一致性測試 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11677e6295956de768c7ebc0c113d775b066bb0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="passing-ole-db-conformance-tests"></a>通過 OLE DB 一致性測試
若要讓提供者更為一致，Data Access SDK 會提供一組 OLE DB 一致性測試。 測試檢查您的提供者的所有層面，並提供您合理做為您提供者函式預期的保證。 您可以在 Microsoft Data Access SDK 中找到 OLE DB 一致性測試。 本節著重於您應該將一致性測試執行。 如需執行 OLE DB 一致性測試的詳細資訊，請參閱 SDK。  
  
## <a name="running-the-conformance-tests"></a>執行一致性測試  
 在 Visual c + + 6.0 中，OLE DB 提供者範本會加入可讓您檢查值和屬性的攔截函式數目。 大部分的這些函式已加入一致性測試的回應。  
  
> [!NOTE]
>  您需要加入您的提供者，才能通過 OLE DB 一致性測試的一些驗證函式。  
  
 此提供者需要兩個驗證常式。 第一個常式`CRowsetImpl::ValidateCommandID`，是您的資料列集類別的一部分。 它會呼叫期間建立的資料列集提供者樣板。 這個範例會使用這個常式告訴取用者不支援索引。 第一個呼叫的是`CRowsetImpl::ValidateCommandID`(請注意，提供者使用 **_RowsetBaseClass** typedef 的介面對應中新增`CMyProviderRowset`中[書籤的提供者支援](../../data/oledb/provider-support-for-bookmarks.md)，因此不需要輸入該樣板引數很長的一行）。 接下來，傳回**DB_E_NOINDEX**如果索引參數不是**NULL** （這表示取用者想要使用我們的索引）。 如需命令 Id 的詳細資訊，請參閱 OLE DB 規格，並尋找**iopenrowset:: Openrowset**。  
  
 下列程式碼是**ValidateCommandID**驗證常式：  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)  
{  
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);  
   if (hr != S_OK)  
      return hr;  
  
   if (pIndexID != NULL)  
      return DB_E_NOINDEX;    // Doesn't support indexes  
  
   return S_OK;  
}  
```  
  
 提供者範本呼叫`OnPropertyChanged`方法只要有人上變更屬性**DBPROPSET_ROWSET**群組。 如果您想要處理的其他群組的屬性，您將它們加入適當的物件 (也就是**DBPROPSET_SESSION**檢查進入`CMyProviderSession`類別)。  
  
 程式碼會先檢查屬性是否連結至另一個。 如果屬性要鏈結，它會設定**DBPROP_BOOKMARKS**屬性設定為 True。 附錄 C 的 OLE DB 規格包含內容的相關資訊。 這項資訊也會告訴您是否要將屬性鏈結至另一個。  
  
 您也可能會想要加入`IsValidValue`常式程式碼。 範本呼叫`IsValidValue`時嘗試設定屬性。 如果您需要額外的處理設定屬性值時，就會覆寫這個方法。 您可以有其中一種方法，每個屬性集。  
  
## <a name="threading-issues"></a>執行緒問題  
 根據預設，OLE DB 提供者中的精靈 ATL OLE DB 提供者精靈會產生要在 apartment 模型中執行的提供者的程式碼。 如果您嘗試執行此程式碼以一致性測試，您一開始就會失敗。 這是因為 Ltm.exe，用來執行 OLE DB 一致性測試，此工具預設為可用執行緒。 OLE DB 提供者精靈程式碼會預設為 apartment 模型的效能和易於使用。  
  
 若要修正這個問題，您可以變更 LTM，或變更的提供者。  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>若要變更 LTM apartment 中執行的執行緒模式  
  
1.  LTM 主功能表上，按一下 **工具**，然後按一下 **選項**。  
  
2.  在**一般**索引標籤上，變更從的執行緒模型**可用執行緒**至**Apartment Threaded**。  
  
 若要變更您的提供者在可用的執行緒模式中執行：  
  
-   在提供者專案中，搜尋的所有執行個體`CComSingleThreadModel`並將它取代為`CComMultiThreadModel`，應該在資料來源、 session 和資料列集標頭。  
  
-   在.rgs 檔案中，變更從的執行緒模型**Apartment**至**兩者**。  
  
-   依照正確的程式設計規則免費執行緒的程式設計 （也就是寫入鎖定）。  
  
## <a name="see-also"></a>另請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)