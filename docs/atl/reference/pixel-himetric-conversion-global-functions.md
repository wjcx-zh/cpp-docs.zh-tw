---
title: "像素 HIMETRIC 轉換全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
dev_langs: C++
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9d670d667345c233fc499cda42194dfafa185dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 轉換全域函式
這些函式提供支援來回轉換像素和 himetric 為單位。  
  
> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlHiMetricToPixel](#atlhimetrictopixel)|將 himetric 為單位 （每一單位為 0.01 公釐） 轉換為像素為單位。|  
|[AtlPixelToHiMetric](#atlpixeltohimetric)|將像素轉換成 himetric 為單位 （每一單位為 0.01 公釐）。|  
  
##  <a name="atlhimetrictopixel"></a>AtlHiMetricToPixel  
 將以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的物件大小轉換成以像素為單位的螢幕裝置大小。  
  
 
```
extern void AtlHiMetricToPixel(
  const SIZEL* lpSizeInHiMetric, 
  LPSIZEL lpSizeInPix);
```  
  
### <a name="parameters"></a>參數  
 `lpSizeInHiMetric`  
 [in]物件，以 himetric 為單位的大小指標。  
  
 `lpSizeInPix`  
 [out]物件的大小，單位為像素所要傳回的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
  
##  <a name="atlpixeltohimetric"></a>AtlPixelToHiMetric  
 將物件在螢幕裝置上以像素為單位的大小，轉換成以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的大小。  
  
```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix, 
    LPSIZEL lpSizeInHiMetric);
```  
  
### <a name="parameters"></a>參數  
 `lpSizeInPix`  
 [in]物件的大小，單位為像素的指標。  
  
 `lpSizeInHiMetric`  
 [out]物件的大小，以 himetric 為單位所要傳回的指標。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]  

### <a name="requirements"></a>需求  
 **標頭：** atlwin.h  

## <a name="see-also"></a>請參閱  
 [函式](../../atl/reference/atl-functions.md)
