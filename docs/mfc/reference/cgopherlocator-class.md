---
title: "CGopherLocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherLocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherLocator class"
  - "gopher locator"
  - "網際網路, gopher searches"
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CGopherLocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從 Gopher 伺服器取得 Gopher 「資源」，判斷定位程式的型別，並使用定位器可用 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)。  
  
> [!NOTE]
>  類別 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成員已被取代，因為它們已經在 Windows XP 平台上不能運作，但是，會繼續在舊版平台運作。  
  
## 語法  
  
```  
class CGopherLocator : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CGopherLocator::CGopherLocator](../Topic/CGopherLocator::CGopherLocator.md)|建構 `CGopherLocator` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CGopherLocator::GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md)|剖析 Gopher 定位器並確定它的屬性。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CGopherLocator::operator LPCTSTR](../Topic/CGopherLocator::operator%20LPCTSTR.md)|直接存取在 `CGopherLocator` 物件中的字元當成 C\+\+. 格式的樣式。|  
  
## 備註  
 無法從該伺服器之前擷取資訊時，應用程式必須取得 Gopher 伺服器的定位程式。  一旦有定位器，它必須將定位程式做為不透明的語彙基元。  
  
 每部 Gopher 定位器會判斷找到的檔案或伺服器類型的屬性。  針對 Gopher 定位器型別清單中看到 [GetLocatorType](../Topic/CGopherLocator::GetLocatorType.md) 。  
  
 應用程式會呼叫方法通常使用定位器至 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md) 擷取特定的資訊片段。  
  
 若要進一步了解 `CGopherLocator` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)