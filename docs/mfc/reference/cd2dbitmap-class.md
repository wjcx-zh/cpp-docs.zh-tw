---
title: "CD2DBitmap 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DBitmap"
  - "CD2DBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBitmap 類別"
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBitmap 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Bitmap 的包裝函式。  
  
## 語法  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|多載。  從 HBITMAP 建構 CD2DBitmap 物件。|  
|[CD2DBitmap::~CD2DBitmap](../Topic/CD2DBitmap::~CD2DBitmap.md)|解構函式。  當正在終結 D2D 點陣圖物件時呼叫。|  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::CD2DBitmap](../Topic/CD2DBitmap::CD2DBitmap.md)|多載。  建構 CD2DBitmap 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::Attach](../Topic/CD2DBitmap::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DBitmap::CopyFromBitmap](../Topic/CD2DBitmap::CopyFromBitmap.md)|將指定的區域從指定的點陣圖複製到目前的點陣圖中|  
|[CD2DBitmap::CopyFromMemory](../Topic/CD2DBitmap::CopyFromMemory.md)|將指定的區域從記憶體複製到目前的點陣圖中|  
|[CD2DBitmap::CopyFromRenderTarget](../Topic/CD2DBitmap::CopyFromRenderTarget.md)|將指定的區域從指定的轉譯目標複製到目前的點陣圖中|  
|[CD2DBitmap::Create](../Topic/CD2DBitmap::Create.md)|建立 CD2DBitmap。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DBitmap::Destroy](../Topic/CD2DBitmap::Destroy.md)|終結 CD2DBitmap 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DBitmap::Detach](../Topic/CD2DBitmap::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DBitmap::Get](../Topic/CD2DBitmap::Get.md)|傳回 ID2D1Bitmap 介面|  
|[CD2DBitmap::GetDPI](../Topic/CD2DBitmap::GetDPI.md)|傳回點陣圖的 Dots Per Inch \(DPI\)。|  
|[CD2DBitmap::GetPixelFormat](../Topic/CD2DBitmap::GetPixelFormat.md)|擷取點陣圖的像素格式和 Alpha 模式|  
|[CD2DBitmap::GetPixelSize](../Topic/CD2DBitmap::GetPixelSize.md)|傳回點陣圖的大小，以與裝置相關的單位 \(像素\) 為單位。|  
|[CD2DBitmap::GetSize](../Topic/CD2DBitmap::GetSize.md)|傳回點陣圖的大小，以裝置獨立畫素 \(DIP\) 為單位。|  
|[CD2DBitmap::IsValid](../Topic/CD2DBitmap::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::CommonInit](../Topic/CD2DBitmap::CommonInit.md)|初始化物件|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::operator ID2D1Bitmap\*](../Topic/CD2DBitmap::operator%20ID2D1Bitmap*.md)|傳回 ID2D1Bitmap 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBitmap::m\_bAutoDestroyHBMP](../Topic/CD2DBitmap::m_bAutoDestroyHBMP.md)|如果應該終結 m\_hBmpSrc，則為 TRUE，否則為 FALSE。|  
|[CD2DBitmap::m\_hBmpSrc](../Topic/CD2DBitmap::m_hBmpSrc.md)|來源點陣圖控制代碼。|  
|[CD2DBitmap::m\_lpszType](../Topic/CD2DBitmap::m_lpszType.md)|資源類型。|  
|[CD2DBitmap::m\_pBitmap](../Topic/CD2DBitmap::m_pBitmap.md)|儲存 ID2D1Bitmap 物件的指標。|  
|[CD2DBitmap::m\_sizeDest](../Topic/CD2DBitmap::m_sizeDest.md)|點陣圖目的地大小。|  
|[CD2DBitmap::m\_strPath](../Topic/CD2DBitmap::m_strPath.md)|點陣圖檔案路徑。|  
|[CD2DBitmap::m\_uiResID](../Topic/CD2DBitmap::m_uiResID.md)|點陣圖資源識別碼。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBitmap](../../mfc/reference/cd2dbitmap-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)