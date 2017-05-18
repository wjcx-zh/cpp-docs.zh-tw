---
title: "COLORADJUSTMENT 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7f88877fa009abf4e811ba0a99b7e0e1683f998a
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT 結構
`COLORADJUSTMENT`結構會定義 Windows 所使用的色彩調整值`StretchBlt`和**stretchdibits 做**函式時`StretchBlt`模式是**半色調**。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct  tagCOLORADJUSTMENT {    /* ca */  
    WORD caSize;  
    WORD caFlags;  
    WORD caIlluminantIndex;  
    WORD caRedGamma;  
    WORD caGreenGamma;  
    WORD caBlueGamma;  
    WORD caReferenceBlack;  
    WORD caReferenceWhite;  
    SHORT caContrast;  
    SHORT caBrightness;  
    SHORT caColorfulness;  
    SHORT caRedGreenTint;  
} COLORADJUSTMENT;  
```  
  
#### <a name="parameters"></a>參數  
 *caSize*  
 以位元組為單位指定的結構大小。  
  
 *caFlags*  
 指定應該如何準備輸出映像。 這個成員可以設定為**NULL**或下列值的任何組合︰  
  
- **CA_NEGATIVE**指定應該顯示原始的映像的負值。  
  
- **CA_LOG_FILTER**指定對數函式應該要套用至最終輸出色彩的密度。 這會增加的色彩對比，較低亮度時。  
  
 *caIlluminantIndex*  
 指定檢視映像物件時的光源的亮度。 這個成員可以設定為下列值之一︰  
  
- **ILLUMINANT_EQUAL_ENERGY**  
  
- **ILLUMINANT_A**  
  
- **ILLUMINANT_B**  
  
- **ILLUMINANT_C**  
  
- **ILLUMINANT_D50**  
  
- **ILLUMINANT_D55**  
  
- **ILLUMINANT_D65**  
  
- **ILLUMINANT_D75**  
  
- **ILLUMINANT_F2**  
  
- **ILLUMINANT_TURNGSTEN**  
  
- **ILLUMINANT_DAYLIGHT**  
  
- **ILLUMINANT_FLUORESCENT**  
  
- **ILLUMINANT_NTSC**  
  
 *caRedGamma*  
 指定來源色彩的紅色主要的第 n 個電源 gamma 修正值。 值必須是介於 2500 65000 之間。 值為 10000 表示 gamma 修正。  
  
 *caGreenGamma*  
 指定來源色彩的綠色主要的第 n 個電源 gamma 修正值。 值必須是介於 2500 65000 之間。 值為 10000 表示 gamma 修正。  
  
 *caBlueGamma*  
 指定來源色彩藍色原色的第 n 個電源 gamma 修正值。 值必須是介於 2500 65000 之間。 值為 10000 表示 gamma 修正。  
  
 *caReferenceBlack*  
 指定來源色彩為黑色的參考。 會比這更深色的任何色彩都會視為黑色。 值必須介於 0 到 4000。  
  
 *caReferenceWhite*  
 指定來源色彩為白色的參考。 任何會比這更亮的色彩會被視為空白。 值必須是介於 6000 到 10000。  
  
 *caContrast*  
 指定要套用至來源物件的對比數量。 值必須介於-100 到 100 之間。 值為 0 表示無對比調整。  
  
 *caBrightness*  
 指定要套用至來源物件的亮度。 值必須介於-100 到 100 之間。 值為 0 表示無亮度調整。  
  
 *caColorfulness*  
 指定要套用至來源物件的 colorfulness 數量。 值必須介於-100 到 100 之間。 值為 0 表示無 colorfulness 調整。  
  
 *caRedGreenTint*  
 指定要套用至來源物件的紅色或綠色濃淡調整數量。 值必須介於-100 到 100 之間。 數字會調整紅色向和負的數字調整綠色向正數。 0 表示無濃淡調整。  
  
## <a name="requirements"></a>需求  
 **標頭︰** wingdi.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)



