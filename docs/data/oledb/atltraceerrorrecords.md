---
title: AtlTraceErrorRecords |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: afea3c3ef1f169e5f1cb5fc675c74b54da1be0d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093343"
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
如果傳回錯誤，傾印 OLE DB 錯誤記錄傾印裝置的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp
      inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);  
```  
  
#### <a name="parameters"></a>參數  
 `hErr`  
 [in]`HRESULT` OLE DB 消費者樣板成員函式所傳回。  
  
## <a name="remarks"></a>備註  
 如果`hErr`不`S_OK`，`AtlTraceErrorRecords`傾印到傾印裝置的 OLE DB 錯誤記錄資訊 (**偵錯** 索引標籤的 輸出 視窗或檔案)。 錯誤記錄資訊，取得提供者，每個錯誤的記錄項目包含資料列數、 來源、 描述、 說明檔、 內容和 GUID。 `AtlTraceErrorRecords` 傾印這項資訊只在偵錯組建。 在發行的組建，它是空白的虛設出最適合。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)