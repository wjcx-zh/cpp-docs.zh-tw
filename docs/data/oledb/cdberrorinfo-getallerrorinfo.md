---
title: "Cdberrorinfo:: Getallerrorinfo |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs: C++
helpviewer_keywords: GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46e233800f814b39e4e14f0b357c381a3e71311e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
傳回錯誤記錄中所包含的所有錯誤資訊類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
      HRESULT GetAllErrorInfo(  
   ULONG ulRecordNum,  
   LCID lcid,  
   BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL  
) const throw( );  
```  
  
#### <a name="parameters"></a>參數  
 *ulRecordNum*  
 [in] 要傳回錯誤資訊之記錄的以零起始數字。  
  
 `lcid`  
 [in] 要傳回之錯誤資訊的地區設定 ID。  
  
 `pbstrDescription`  
 [out] 如果不支援地區設定，則傳回錯誤的文字描述指標或 NULL。 請參閱＜備註＞。  
  
 `pbstrSource`  
 [out] 包含產生錯誤之元件名稱的字串指標。  
  
 `pguid`  
 [out] 定義錯誤之介面的 GUID 指標。  
  
 *pdwHelpContext*  
 [out] 錯誤的說明主題內容識別碼指標。  
  
 *pbstrHelpFile*  
 [out] 包含描述錯誤說明檔路徑之字串的指標。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為 `S_OK`。 請參閱[ierrorrecords:: Geterrorinfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx)中*OLE DB 程式設計人員參考*如需其他傳回值。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="remarks"></a>備註  
 `pbstrDescription` 的輸出值是藉由呼叫 IErrorInfo::GetDescription 從內部取得，如果不支援地區設定或下列兩個條件都成立，則將值設為 NULL：  
  
1.  值`lcid`不是美國英文和  
  
2.  `lcid` 的值與 GetUserDefaultLCID 所傳回的值「不」相等。  
  
## <a name="see-also"></a>請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)