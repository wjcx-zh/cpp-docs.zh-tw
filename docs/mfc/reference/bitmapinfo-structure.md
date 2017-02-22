---
title: "BITMAPINFO 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BITMAPINFO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BITMAPINFO 結構"
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# BITMAPINFO 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`BITMAPINFO` 結構定義大小和色彩資訊 Windows 與裝置無關的點陣圖的 \(DIB\)。  
  
## 語法  
  
```  
typedef struct tagBITMAPINFO {  
   BITMAPINFOHEADER bmiHeader;  
   RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### 參數  
 `bmiHeader`  
 指定包含與裝置無關點陣圖的大小和色彩格式資訊的 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) 結構。  
  
 `bmiColors`  
 指定陣列或 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) 定義點陣圖色彩的 `DWORD` 資料型別。  
  
## 備註  
 與裝置無關點陣圖包含兩個不同的部分:描述點陣圖的大小和色彩的 `BITMAPINFO` 結構和點陣圖中指定像素的位元組陣列。  一起包裝陣列中的位元組，，但是在 `LONG` 界限必須填補每條掃描線以零結束。  如果高度是正數，點陣圖的原點位於左下角。  如果高度是負數，原點是左上角。  
  
 *封裝點陣圖* 是位元組陣列緊接在 `BITMAPINFO` 結構的點陣圖。  封裝點陣圖是由單一指標參考。  
  
 如需 `BITMAPINFO` 結構和適當值的詳細資訊 `BITMAPINFOHEADER` 和 `RGBQUAD` 結構成員的詳細資訊，請參閱下列在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 文件的主題。  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="b5dd2e8c9cedbac12eb858bd01a029a2" class\="tgtSentence"\>BITMAPINFO 結構\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
-   [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376) 結構  
  
-   [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938) 結構  
  
## 需求  
 **標頭檔：** wingdi.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)