---
title: "RGNDATA 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RGNDATA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RGNDATA 結構"
ms.assetid: 72257c00-f440-4dca-979e-9b6b5b2d5f2f
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RGNDATA 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`RGNDATA` 結構包含標頭和組成區域的矩形陣列。 這些由上而下由左至右排序的矩形不會重疊。  
  
## <a name="syntax"></a>語法  
  
```  
 
    typedef struct _RGNDATA { /* rgnd */  
    RGNDATAHEADER rdh;  
    char Buffer[1];  
} RGNDATA;  
```  
  
#### <a name="parameters"></a>參數  
 *rdh*  
 指定 [RGNDATAHEADER](http://msdn.microsoft.com/library/windows/desktop/dd162941) 結構。 (如需這個結構的詳細資訊，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)])。這個結構的成員指定區域類型 (它是否為矩形或梯形)、組成區域的矩形數量和包含矩形結構的緩衝區大小等等。  
  
 `Buffer`  
 指定包含任意大小的緩衝區 [RECT](../../mfc/reference/rect-structure1.md) 組成區域的結構。  
  
## <a name="requirements"></a>需求  
 **標頭︰** wingdi.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRgn::CreateFromData](../../mfc/reference/crgn-class.md#CreateFromData)   
 [CRgn::GetRegionData](../../mfc/reference/crgn-class.md#GetRegionData)

