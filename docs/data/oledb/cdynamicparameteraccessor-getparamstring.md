---
title: "CDynamicParameterAccessor::GetParamString | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicParameterAccessor.GetParamString"
  - "GetParamString"
  - "CDynamicParameterAccessor::GetParamString"
  - "ATL.CDynamicParameterAccessor.GetParamString"
  - "ATL::CDynamicParameterAccessor::GetParamString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParamString 方法"
ms.assetid: 078c2b1c-7072-47c1-a203-f47e75363f91
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDynamicParameterAccessor::GetParamString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取在緩衝區中的指定參數的字串資料。  
  
## 語法  
  
```  
  
      bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringA& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CSimpleStringW& strOutput  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   CHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
bool GetParamString(  
   DBORDINAL nParam,  
   WCHAR* pBuffer,  
   size_t* pMaxLen  
) throw( );  
```  
  
#### 參數  
 `nParam`  
 \[in\] 參數的數目 \(從 1 開始位移\)。  參數 0 為傳回值。  參數的數目是根據其在 SQL 或預存程序呼叫順序的參數的索引。  如需範例，請參閱 [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)。  
  
 `strOutput`  
 \[out\] ANSI \(**CSimpleStringA**\) 或 Unicode \(**CSimpleStringW**\) 指定參數的字串資料。  您應該傳遞 `CString`型別參數，例如：  
  
 [!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/CPP/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
 `pBuffer`  
 \[out\] 為 ANSI \(**CHAR**\) 或 Unicode \(**WCHAR**\) 指定參數的字串資料之的指標。  
  
 `pMaxLen`  
 \[out\] 緩衝區的大小的指標指向 `pBuffer` \(以字元為單位\)，包括結束的 null\)。  
  
## 備註  
 如果成功則傳回 **true**，失敗則傳回 **false**。  
  
 如果 `pBuffer` 是空的，這個方法會設定在記憶體中所需的緩衝區大小所指向的 `pMaxLen` 並傳回 **true** ，而不複製資料。  
  
 如果緩衝區 `pBuffer` 不夠大包含整個字串，這個方法會失敗。  
  
 使用 `GetParamString` 緩衝區擷取字串參數資料。  使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 在緩衝區擷取非字串參數資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)