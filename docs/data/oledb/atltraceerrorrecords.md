---
title: "AtlTraceErrorRecords |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
dev_langs: C++
helpviewer_keywords: AtlTraceErrorRecords function
ms.assetid: b83970b3-dc2a-445c-9142-f52218719905
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 696d00e32ebf692d8155b93247f3ca83b0bb2b08
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords
如果傳回錯誤，傾印 OLE DB 錯誤記錄傾印裝置的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
  
      inline void AtlTraceErrorRecords(   
   HRESULT hrErr = S_OK    
);  
```  
  
#### <a name="parameters"></a>參數  
 `hErr`  
 [in]`HRESULT` OLE DB 消費者樣板成員函式所傳回。  
  
## <a name="remarks"></a>備註  
 如果`hErr`不`S_OK`，`AtlTraceErrorRecords`傾印到傾印裝置的 OLE DB 錯誤記錄資訊 (**偵錯** 索引標籤的 輸出 視窗或檔案)。 錯誤記錄資訊，取得提供者，每個錯誤的記錄項目包含資料列數、 來源、 描述、 說明檔、 內容和 GUID。 `AtlTraceErrorRecords`傾印這項資訊只在偵錯組建。 在發行的組建，它是空白的虛設出最適合。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域函式的 OLE DB 消費者樣板](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)