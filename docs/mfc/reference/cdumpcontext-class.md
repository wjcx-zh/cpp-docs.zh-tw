---
title: "CDumpContext Class | Microsoft Docs"
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
  - "CDumpContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxDump object"
  - "CDumpContext class"
  - "診斷, diagnostic classes"
  - "diagnostic classes"
  - "診斷, diagnostic classes"
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDumpContext Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以人們可讀取的文字格式，支援內部資料流導向的診斷輸出。  
  
## 語法  
  
```  
class CDumpContext  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDumpContext::CDumpContext](../Topic/CDumpContext::CDumpContext.md)|建構 `CDumpContext` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDumpContext::DumpAsHex](../Topic/CDumpContext::DumpAsHex.md)|以十六進位格式傾印所表示的項目。|  
|[CDumpContext::Flush](../Topic/CDumpContext::Flush.md)|清除在傾印內容緩衝區的任何資料。|  
|[CDumpContext::GetDepth](../Topic/CDumpContext::GetDepth.md)|取得整數與傾印對應的深度。|  
|[CDumpContext::HexDump](../Topic/CDumpContext::HexDump.md)|以十六進位格式傾印在陣列中的位元組。|  
|[CDumpContext::SetDepth](../Topic/CDumpContext::SetDepth.md)|將傾印的深度。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CDumpContext::operator \<\<](../Topic/CDumpContext::operator%20%3C%3C.md)|插入變數和物件傾印至內容。|  
  
## 備註  
 `CDumpContext` 不具有基底類別。  
  
 您可以針對大部分傾印使用 [afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md)，一 predeclared `CDumpContext` 物件。  `afxDump` 物件只有 MFC 程式庫的偵錯版本。  
  
 將其輸出的記憶體 [診斷服務](../../mfc/reference/diagnostic-services.md) 使用 `afxDump` 。  
  
 在  視窗中環境下，從預先定義的 `afxDump` 物件的輸出，概念類似於 `cerr` 資料流，傳送至偵錯工具會透過 Windows 函式 **OutputDebugString**。  
  
 `CDumpContext` 類別含有傾印物件的資料 `CObject` 指標的多載**\<\<**插入 \(\) 運算子。  如果您需要的衍生物件的自訂傾印格式，請覆寫 [CObject::Dump](../Topic/CObject::Dump.md)。  大部分 Microsoft Foundation Classes 實作類別的覆寫 `Dump` 成員函式。  
  
 從 `CObject`並非衍生自類別，例如 `CString`， `CTime`和 `CTimeSpan`的類別，具有自己的多載 `CDumpContext` 插入運算子，例如常用的結構 \(例如 **CFileStatus**、 `CPoint`和 `CRect`。  
  
 如果您在類別中實作使用 [IMPLEMENT\_DYNAMIC](../Topic/IMPLEMENT_DYNAMIC.md) 或 [IMPLEMENT\_SERIAL](../Topic/IMPLEMENT_SERIAL.md) 巨集，則 `CObject::Dump` 會列印出 `CObject`名稱衍生類別。  否則，仍會列印 `CObject`。  
  
 `CDumpContext` 類別對程式庫的兩個偵錯版本和發行版本所提供的，不過， `Dump` 成員函式在偵錯版本只會定義。  使用 **\#ifdef \_DEBUG** \/ `#endif` 陳述式括住您的診斷程式碼，包括您的自訂 `Dump` 成員函式。  
  
 在您建立 `CDumpContext` 物件之前，您必須建立做為傾印的目的 `CFile` 物件。  
  
 如需 `CDumpContext`的資訊，請參閱 [偵錯 MFC 應用程式](../Topic/MFC%20Debugging%20Techniques.md)。  
  
 **\#define \_DEBUG**  
  
## 繼承階層架構  
 `CDumpContext`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)