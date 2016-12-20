---
title: "COleException Class | Microsoft Docs"
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
  - "COleException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleException class"
  - "例外狀況, OLE"
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleException Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示例外狀況與 OLE 作業相關。  
  
## 語法  
  
```  
class COleException : public CException  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleException::Process](../Topic/COleException::Process.md)|轉譯攔截的例外狀況為 OLE 傳回碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleException::m\_sc](../Topic/COleException::m_sc.md)|表示包含例外狀況原因的狀態碼。|  
  
## 備註  
 `COleException` 類別包含保存表示例外狀況的狀態碼原因的一個公用資料成員。  
  
 一般而言，您不應該直接建立物件， `COleException` 相反地，您應該呼叫 [AfxThrowOleException](../Topic/AfxThrowOleException.md)。  
  
 如需例外狀況的詳細資訊，請參閱 Microsoft 知識庫文件 [例外處理 \(MFC\)](../../mfc/exception-handling-in-mfc.md) 和 [例外狀況:OLE 例外狀況。](../../mfc/exceptions-ole-exceptions.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [MFC 範例 CALCDRIV](../../top/visual-cpp-samples.md)   
 [CException Class](../../mfc/reference/cexception-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)