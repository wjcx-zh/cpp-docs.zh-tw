---
title: "ATL 編碼方式參考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "編碼"
  - "編碼, 函式"
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ATL 編碼方式參考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在一般網際網路標準範圍的編碼方式 \(例如 uuencode、十六進位和 UTF8 由 atlenc.h 中所找到的程式碼支援。  
  
### 功能  
  
|||  
|-|-|  
|[AtlGetHexValue](../Topic/AtlGetHexValue.md)|呼叫此函式來取得十六進位數字的數值。|  
|[AtlHexDecode](../Topic/AtlHexDecode.md)|解碼已編碼為十六進位文字 \(例如 \[ [AtlHexEncode](../Topic/AtlHexEncode.md)\) 的呼叫資料的字串。|  
|[AtlHexDecodeGetRequiredLength](../Topic/AtlHexDecodeGetRequiredLength.md)|呼叫此函式來取得大小可以包含從所指定長度的十六進位編碼字串解碼的資料緩衝區中的位元組數。|  
|[AtlHexEncode](../Topic/AtlHexEncode.md)|呼叫這個函式進入某些資料以十六進位的文字字串。|  
|[AtlHexEncodeGetRequiredLength](../Topic/AtlHexEncodeGetRequiredLength.md)|呼叫此函式來取得可包含從所指定大小的資料輸入之字串緩衝區的大小。|  
|[AtlUnicodeToUTF8](../Topic/AtlUnicodeToUTF8.md)|呼叫此函式將 Unicode 字串轉換為 UTF\-8。|  
|[BEncode](../Topic/BEncode.md)|使用「B」編碼方式，呼叫這個函式轉換一些資料。|  
|[BEncodeGetRequiredLength](../Topic/BEncodeGetRequiredLength.md)|呼叫此函式來取得可包含從所指定大小的資料輸入之字串緩衝區的大小。|  
|[EscapeXML](../Topic/EscapeXML.md)|呼叫這個函式會轉換為 unsafe 用於 XML 為其安全對等的字元。|  
|[GetExtendedChars](../Topic/GetExtendedChars.md)|呼叫此函式來取得擴充字元數目的字串。|  
|[IsExtendedChar](../Topic/IsExtendedChar.md)|呼叫這個函式會發現，如果指定的字元是否為擴充字元 \(小於 32\)，大於 126，而非定位字元、換行字元、歸位字元 \(Carriage Return\)|  
|[QEncode](../Topic/QEncode.md)|使用「Q」編碼方式，呼叫這個函式轉換一些資料。|  
|[QEncodeGetRequiredLength](../Topic/QEncodeGetRequiredLength.md)|呼叫此函式來取得可包含從所指定大小的資料輸入之字串緩衝區的大小。|  
|[QPDecode](../Topic/QPDecode.md)|將引號可列印的格式輸入 [QPEncode](../Topic/QPEncode.md)等\) 的呼叫資料的字串。|  
|[QPDecodeGetRequiredLength](../Topic/QPDecodeGetRequiredLength.md)|呼叫此函式來取得大小可以包含從所指定長度的引號可列印編碼字串解碼的資料緩衝區中的位元組數。|  
|[QPEncode](../Topic/QPEncode.md)|呼叫這個函式會在引號可列印之格式的資料。|  
|[QPEncodeGetRequiredLength](../Topic/QPEncodeGetRequiredLength.md)|呼叫此函式來取得可包含從所指定大小的資料輸入之字串緩衝區的大小。|  
|[UUDecode](../Topic/UUDecode.md)|解碼 uuencoded 等 [UUEncode](../Topic/UUEncode.md)\) 的呼叫資料的字串。|  
|[UUDecodeGetRequiredLength](../Topic/UUDecodeGetRequiredLength.md)|呼叫此函式來取得大小可以包含從所指定長度的字串 uuencoded 解密資料緩衝區中的位元組數。|  
|[UUEncode](../Topic/UUEncode.md)|呼叫這個函式會 uuencode 一些資料。|  
|[UUEncodeGetRequiredLength](../Topic/UUEncodeGetRequiredLength.md)|呼叫此函式來取得可包含從所指定大小的資料輸入之字串緩衝區的大小。|  
  
### 巨集  
  
|||  
|-|-|  
|[ATL\_ESC 旗標。](../Topic/ATL_ESC%20Flags.md)|這些旗標可用來控制 [EscapeXML](../Topic/EscapeXML.md)行為。|  
|[ATLSMTP\_QPENCODE 旗標。](../Topic/ATLSMTP_QPENCODE%20Flags.md)|這些旗標描述引號可列印的編碼方式。 [QPEncode](../Topic/QPEncode.md)執行。|  
|[ATLSMTP\_UUENCODE 旗標。](../Topic/ATLSMTP_UUENCODE%20Flags.md)|這些旗標的描述 uuencoding 方式。 [UUEncode](../Topic/UUEncode.md)執行。|  
  
## 請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../atl/atl-com-desktop-components.md)