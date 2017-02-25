---
title: "CDBErrorInfo::GetAllErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CDBErrorInfo.GetAllErrorInfo"
  - "CDBErrorInfo::GetAllErrorInfo"
  - "ATL::CDBErrorInfo::GetAllErrorInfo"
  - "GetAllErrorInfo"
  - "CDBErrorInfo.GetAllErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAllErrorInfo 方法"
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDBErrorInfo::GetAllErrorInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回錯誤記錄檔中的錯誤資訊的所有型別。  
  
## 語法  
  
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
  
#### 參數  
 *ulRecordNum*  
 \[in\] 的傳回錯誤資訊以零為基礎數字的記錄。  
  
 `lcid`  
 \[in\] 要傳回的錯誤資訊的地區設定 ID。  
  
 `pbstrDescription`  
 \[out\] 如果地區設定不支援，錯誤或空白文字描述的指標。  請參閱＜備註＞。  
  
 `pbstrSource`  
 \[out\] 包含產生錯誤的元件名稱之字串的指標。  
  
 `pguid`  
 \[out\] 定義錯誤介面的 GUID 的指標。  
  
 *pdwHelpContext*  
 \[out\] 錯誤的說明內容識別碼的指標。  
  
 *pbstrHelpFile*  
 \[out\] 包含描述錯誤的說明檔路徑之字串的指標。  
  
## 傳回值  
 如果成功，則為 `S_OK`。  為其他傳回值請參閱《*OLE DB 程式設計人員參考*》的[IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 備註  
 `pbstrDescription` 的輸出值由呼叫 IErrorInfo::GetDescription 內部取得，如果地區設定不支援或下列兩個條件都成立則將值設為 null：  
  
1.  `lcid` 的值不是美國英文且  
  
2.  `lcid` 的值與 GetUserDefaultLCID 傳回的值不相等。  
  
## 請參閱  
 [CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)