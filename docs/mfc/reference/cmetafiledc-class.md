---
title: "CMetaFileDC Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMetaFileDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMetaFileDC class"
  - "中繼檔, 實作"
  - "Windows metafiles [C++]"
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMetaFileDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作一個 Windows 中繼檔，其中包含圖形裝置介面 \(GDI\) 序列命令可以重新執行建立所需的影像或文字。  
  
## 語法  
  
```  
class CMetaFileDC : public CDC  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMetaFileDC::CMetaFileDC](../Topic/CMetaFileDC::CMetaFileDC.md)|建構 `CMetaFileDC` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMetaFileDC::Close](../Topic/CMetaFileDC::Close.md)|關閉裝置內容並建立中繼檔控制代碼。|  
|[CMetaFileDC::CloseEnhanced](../Topic/CMetaFileDC::CloseEnhanced.md)|關閉加強型中繼檔 \(Metafile\) 裝置內容並建立加強型中繼檔控制代碼。|  
|[CMetaFileDC::Create](../Topic/CMetaFileDC::Create.md)|建立 Windows 中繼檔 \(Metafile\) 裝置內容並將其附加至 `CMetaFileDC` 物件。|  
|[CMetaFileDC::CreateEnhanced](../Topic/CMetaFileDC::CreateEnhanced.md)|建立加強型格式中繼檔的中繼檔 \(Metafile\) 裝置內容。|  
  
## 備註  
 若要實作 Windows 中繼檔，請先建立 `CMetaFileDC` 物件。  `CMetaFileDC` 叫用建構函式，然後 [建立](../Topic/CMetaFileDC::Create.md) 呼叫成員函式，建立 Windows 中繼檔 \(Metafile\) 裝置內容並將其附加至 `CMetaFileDC` 物件。  
  
 接下來將 `CDC` GDI 序列命令的物件 `CMetaFileDC` 您為它想要重新執行。  建立輸出，例如 `MoveTo` 和 `LineTo`只能使用的 GDI 命令。  
  
 在您想要傳送命令至中繼檔後，請呼叫 **關閉** 成員函式，結束中繼檔 \(Metafile\) 裝置內容並將中繼檔控制代碼。  然後處理 `CMetaFileDC` 物件。  
  
 [CDC::PlayMetaFile](../Topic/CDC::PlayMetaFile.md) 可使用的中繼檔控制代碼重複播放此中繼檔。  中繼檔可由 Windows 函式也 [CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)作業 \(例如，將一個中繼檔儲存至磁碟。  
  
 在此中繼檔不再需要物件時，請將其刪除從與 [DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows 函式的記憶體。  
  
 您也可以實作 `CMetaFileDC` 物件，讓它能夠處理輸出的呼叫和屬性 \(Attribute\) GDI 呼叫 \(例如 `GetTextExtent`。  此類中繼檔具有更大的彈性，因此可以更輕鬆地重複使用 GDI 一般程式碼，通常包括輸出的混合，該屬性會呼叫。  `CMetaFileDC` 類別繼承這兩個裝置內容， `m_hDC` 和 `m_hAttribDC`，從 `CDC`。  `m_hDC` 裝置內容處理所有 [CDC](../../mfc/reference/cdc-class.md) GDI 輸出呼叫和 `m_hAttribDC` 裝置內容控制代碼所有 `CDC` GDI 屬性呼叫。  通常，這兩個裝置內容參考相同的裝置。  預設會在 `CMetaFileDC`情況下，屬性 DC 設為 **NULL** 。  
  
 刪除中繼檔以外，建立指向螢幕、印表機或裝置的第二個裝置內容，然後呼叫 `SetAttribDC` 成員函式使新的裝置內容。 `m_hAttribDC`。  GDI 呼叫以取得資訊就會被導向至新的 `m_hAttribDC`。  輸出 GDI 呼叫會移至 `m_hDC`，表示中繼檔。  
  
 如需 `CMetaFileDC`的資訊，請參閱 [裝置內容。](../../mfc/device-contexts.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## 需求  
 **Header:** afxext.h  
  
## 請參閱  
 [CDC 類別](../../mfc/reference/cdc-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)