---
title: 'Crowset:: Findnextrow |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CRowset.FindNextRow
- CRowset<TAccessor>.FindNextRow
- ATL::CRowset::FindNextRow
- CRowset::FindNextRow
- CRowset<TAccessor>::FindNextRow
- CRowset.FindNextRow
- ATL.CRowset<TAccessor>.FindNextRow
- ATL::CRowset<TAccessor>::FindNextRow
- FindNextRow
dev_langs:
- C++
helpviewer_keywords:
- FindNextRow method
ms.assetid: 36484df9-3625-4f15-bf69-db73a8d91c55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4afc1db20970102ecddb9031f4f1b7a8f6906cf4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetfindnextrow"></a>CRowset::FindNextRow
尋找指定的書籤之後的下一個相符的資料列。  
  
## <a name="syntax"></a>語法  
  
```
HRESULT FindNextRow(DBCOMPAREOP op,   
  BYTE* pData,   
   DBTYPE wType,   
   DBLENGTH nLength,   
   BYTE bPrecision,   
   BYTE bScale,   
   BOOL bSkipCurrent = TRUE,   
   CBookmarkBase* pBookmark = NULL) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `op`  
 [in]要用於比較資料列值的作業。 如需值，請參閱[irowsetfind:: Findnextrow](https://msdn.microsoft.com/en-us/library/ms723091.aspx)。  
  
 `pData`  
 [in]要比對值的指標。  
  
 `wType`  
 [in]表示緩衝區的值部分的資料類型。 類型指標的相關資訊，請參閱[資料型別](https://msdn.microsoft.com/en-us/library/ms723969.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
 `nLength`  
 [in]取用者的資料結構配置資料值的長度，以位元組為單位。 如需詳細資訊，請參閱描述**cbMaxLen**中[DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)中*OLE DB 程式設計人員參考。*  
  
 `bPrecision`  
 [in]取得資料時使用的最大有效位數。 使用的唯有`wType`是`DBTYPE_NUMERIC`。 如需詳細資訊，請參閱[涉及 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL 轉換](https://msdn.microsoft.com/en-us/library/ms719714.aspx)中*OLE DB 程式設計人員參考*。  
  
 `bScale`  
 [in]取得資料時使用小數位數。 使用的唯有`wType`是`DBTYPE_NUMERIC`或**DBTYPE_DECIMAL**。 如需詳細資訊，請參閱[涉及 DBTYPE_NUMERIC 或 DBTYPE_DECIMAL 轉換](https://msdn.microsoft.com/en-us/library/ms719714.aspx)中*OLE DB 程式設計人員參考*。  
  
 *bSkipCurrent*  
 [in]從 開始搜尋的書籤的資料列數目。  
  
 `pBookmark`  
 [in]要開始搜尋位置的書籤。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 此方法需要的選擇性介面**IRowsetFind**，這可能不支援所有提供者; 如果這種情況，方法會傳回**E_NOINTERFACE**。 您也必須設定**DBPROP_IRowsetFind**至`VARIANT_TRUE`之前先呼叫**開啟**的資料表上包含資料列集的命令。  
  
 使用書籤中取用者的相關資訊，請參閱[使用書籤](../../data/oledb/using-bookmarks.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [CRowset 類別](../../data/oledb/crowset-class.md)   
 [DBBINDING 結構](https://msdn.microsoft.com/en-us/library/ms716845.aspx)