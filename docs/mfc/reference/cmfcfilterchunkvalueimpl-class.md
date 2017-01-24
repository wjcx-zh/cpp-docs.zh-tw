---
title: "CMFCFilterChunkValueImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFilterChunkValueImpl"
  - "afxwin/CMFCFilterChunkValueImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFilterChunkValueImpl class"
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCFilterChunkValueImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這是為了簡化區塊和屬性值的邏輯的類別。  
  
## 語法  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl.md)|自動終結物件。|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](../Topic/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl.md)|建構物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::Clear](../Topic/CMFCFilterChunkValueImpl::Clear.md)|清除 ChunkValue。|  
|[CMFCFilterChunkValueImpl::CopyChunk](../Topic/CMFCFilterChunkValueImpl::CopyChunk.md)|複製這個區塊為描述大量記憶體的結構。|  
|[CMFCFilterChunkValueImpl::CopyFrom](../Topic/CMFCFilterChunkValueImpl::CopyFrom.md)|初始化從另一個值的這個區塊中的值。|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](../Topic/CMFCFilterChunkValueImpl::GetChunkGUID.md)|擷取大量 GUID。|  
|[CMFCFilterChunkValueImpl::GetChunkPID](../Topic/CMFCFilterChunkValueImpl::GetChunkPID.md)|擷取大量 PID \(屬性 ID\)。|  
|[CMFCFilterChunkValueImpl::GetChunkType](../Topic/CMFCFilterChunkValueImpl::GetChunkType.md)|取得區塊型別。|  
|[CMFCFilterChunkValueImpl::GetString](../Topic/CMFCFilterChunkValueImpl::GetString.md)|擷取字串值。|  
|[CMFCFilterChunkValueImpl::GetValue](../Topic/CMFCFilterChunkValueImpl::GetValue.md)|擷取值做為配置的 propvariant。|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](../Topic/CMFCFilterChunkValueImpl::GetValueNoAlloc.md)|傳回非配置 \(內部值\) 值。|  
|[CMFCFilterChunkValueImpl::IsValid](../Topic/CMFCFilterChunkValueImpl::IsValid.md)|檢查這個屬性值是否有效。|  
|[CMFCFilterChunkValueImpl::SetBoolValue](../Topic/CMFCFilterChunkValueImpl::SetBoolValue.md)|多載。  依據索引鍵設定屬性為布林值。|  
|[CMFCFilterChunkValueImpl::SetDwordValue](../Topic/CMFCFilterChunkValueImpl::SetDwordValue.md)|依據索引鍵屬性設為 DWORD。|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](../Topic/CMFCFilterChunkValueImpl::SetFileTimeValue.md)|依據索引鍵將屬性設定為 filetime。|  
|[CMFCFilterChunkValueImpl::SetInt64Value](../Topic/CMFCFilterChunkValueImpl::SetInt64Value.md)|依據索引鍵屬性設為 int64。|  
|[CMFCFilterChunkValueImpl::SetIntValue](../Topic/CMFCFilterChunkValueImpl::SetIntValue.md)|依據索引鍵屬性設為 int。|  
|[CMFCFilterChunkValueImpl::SetLongValue](../Topic/CMFCFilterChunkValueImpl::SetLongValue.md)|依據索引鍵屬性設為長度。|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](../Topic/CMFCFilterChunkValueImpl::SetSystemTimeValue.md)|依據索引鍵將屬性設定為 SystemTime。|  
|[CMFCFilterChunkValueImpl::SetTextValue](../Topic/CMFCFilterChunkValueImpl::SetTextValue.md)|依據索引鍵屬性設為 Unicode 字串。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCFilterChunkValueImpl::SetChunk](../Topic/CMFCFilterChunkValueImpl::SetChunk.md)|將大量的通用屬性的 Helper 函式。|  
  
## 備註  
 若要使用，您建立正確型別的 CMFCFilterChunkValueImpl 類別  
  
 範例：  
  
 CMFCFilterChunkValueImpl 區塊，  
  
 chunk.SetBoolValue hr \= \(PKEY\_IsAttachment， true\);  
  
 或  
  
 chunk.SetFileTimeValue hr \= \(PKEY\_ItemDate， ftLastModified\);  
  
## 繼承階層架構  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## 需求  
 **標頭檔：**afxwin.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)