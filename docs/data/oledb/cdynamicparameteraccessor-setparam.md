---
title: "CDynamicParameterAccessor::SetParam | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDynamicParameterAccessor::SetParam"
  - "ATL::CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor.SetParam"
  - "ATL.CDynamicParameterAccessor.SetParam"
  - "SetParam"
  - "CDynamicParameterAccessor:SetParam"
  - "CDynamicParameterAccessor::SetParam<ctype>"
  - "CDynamicParameterAccessor::SetParam"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParam 方法"
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CDynamicParameterAccessor::SetParam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指定的 \(非字串\) 資料，請將參數設定為緩衝區。  
  
## 語法  
  
```  
  
      template < class   
      ctype >  
bool SetParam(  
   DBORDINAL nParam,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
template < class ctype >  
bool SetParam(  
   TCHAR* pParamName,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
```  
  
#### 參數  
 `ctype`  
 是資料型別的範本參數。  
  
 `nParam`  
 \[參數的數目 \(從 1\) 的位移。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 \[in\] 參數名稱。  
  
 `pData`  
 \[out 包含資料的記憶體的指標會寫入緩衝區。  
  
 *status*  
 \[ `DBSTATUS` 的狀態。  如需 `DBSTATUS` 值的詳細資訊，請參閱《 *OLE DB 程式設計人員參考》的*[狀態](https://msdn.microsoft.com/en-us/library/ms722617.aspx) 或搜尋 oledb.h 的 `DBSTATUS` 。  
  
## 傳回值  
 在成功傳回 **true** 和 **false** 發生錯誤。  
  
 使用 `SetParam` 設定緩衝區的非字串參數資料。  使用 [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) 將資料從緩衝區的參數資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)