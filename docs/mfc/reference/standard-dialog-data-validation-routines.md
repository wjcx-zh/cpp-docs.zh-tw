---
title: "標準對話方塊資料驗證常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33566bcdfab1a618dc8ff79deb375b3f9d1221f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="standard-dialog-data-validation-routines"></a>標準對話方塊資料驗證常式
本主題列出用於通用的 MFC 對話方塊控制項的標準對話方塊資料驗證 (DDV) 常式。  
  
> [!NOTE]
>  標準對話方塊資料交換常式定義於標頭檔 afxdd_.h。 不過，應用程式應該包括 afxwin.h。  
  
### <a name="ddv-functions"></a>DDV 函式  
  
|||  
|-|-|  
|[DDV_MaxChars](#ddv_maxchars)|確認指定的控制項值中的字元數目不超過指定的最大值。|  
|[DDV_MinMaxByte](#ddv_minmaxbyte)|確認指定的控制項值不會超過給定**位元組**範圍。|  
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|確認指定的控制項值未超過給定的時間範圍。|  
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|確認指定的控制項值不會超過給定**double**範圍。|  
|[DDV_MinMaxDWord](#ddv_minmaxdword)|確認指定的控制項值不會超過給定**DWORD**範圍。|  
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|確認指定的控制項值不會超過給定**float**範圍。|  
|[DDV_MinMaxInt](#ddv_minmaxint)|確認指定的控制項值不會超過給定**int**範圍。|  
|[DDV_MinMaxLong](#ddv_minmaxlong)|確認指定的控制項值不會超過給定**長**範圍。|  
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|確認指定的控制項值不會超過給定**LONGLONG**範圍。|  
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|確認指定的控制項值未超過指定的日期範圍內。|  
|[DDV_MinMaxShort](#ddv_minmaxshort)|確認指定的控制項值不會超過給定**簡短**範圍。|  
|[DDV_MinMaxSlider](#ddv_minmaxslider)|確認指定的滑桿控制項值落在指定範圍內。|  
|[DDV_MinMaxUInt](#ddv_minmaxuint)|確認指定的控制項值不會超過給定**UINT**範圍。|  
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|確認指定的控制項值介於兩個指定的值。| 
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|確認指定的控制項值不會超過給定**ULONGLONG**範圍。|  
  

  
##  <a name="ddv_maxchars"></a>DDV_MaxChars  
 呼叫`DDV_MaxChars`驗證與關聯的控制項中的字元數*值*不超過*nChars*。  
  
```   
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,  
    CString const& value,  
    int nChars); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `nChars`  
 允許的字元數目上限。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxbyte"></a>DDV_MinMaxByte  
 呼叫`DDV_MinMaxByte`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,  
    BYTE value,  
    BYTE minVal,  
    BYTE maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**位元組**) 允許。  
  
 `maxVal`  
 最大值 (類型的**位元組**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime  
 呼叫`DDV_MinMaxDateTime`確認日期和時間選擇器中的日期/時間值，控制 ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) 相關聯*refValue*介於`refMinRange`和`refMaxRange`。  
  
```   
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。 您不需要刪除此物件。  
  
 *refValue*  
 若要參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)或[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)對話方塊、 表單檢視或控制項檢視物件的成員變數與相關聯的物件。 此物件包含要驗證資料。  
  
 `refMinRange`  
 最小日期/時間允許的值。  
  
 `refMaxRange`  
 允許的最大日期/時間值。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble  
 呼叫`DDV_MinMaxDouble`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,  
    double const& value,  
    double minVal,  
    double maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**double**) 允許。  
  
 `maxVal`  
 最大值 (類型的**double**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxdword"></a>DDV_MinMaxDWord  
 呼叫`DDV_MinMaxDWord`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,  
    DWORD const& value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的`DWORD`) 允許。  
  
 `maxVal`  
 最大值 (類型的`DWORD`) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat  
 呼叫`DDV_MinMaxFloat`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,  
    float value,  
    float minVal,  
    float maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**float**) 允許。  
  
 `maxVal`  
 最大值 (類型的**float**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxint"></a>DDV_MinMaxInt  
 呼叫`DDV_MinMaxInt`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,  
    int value,  
    int minVal,  
    int maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的`int`) 允許。  
  
 `maxVal`  
 最大值 (類型的`int`) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxlong"></a>DDV_MinMaxLong  
 呼叫`DDV_MinMaxLong`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,  
    long value,  
    long minVal,  
    long maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**長**) 允許。  
  
 `maxVal`  
 最大值 (類型的**長**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong  
 呼叫`DDV_MinMaxLongLong`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,  
    LONGLONG value,  
    LONGLONG minVal,  
    LONGLONG maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**LONGLONG**) 允許。  
  
 `maxVal`  
 最大值 (類型的**LONGLONG**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth  
 呼叫`DDV_MinMaxMonth`以確認月份行事曆中的日期/時間值，控制 ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) 相關聯*refValue*介於`refMinRange`和`refMaxRange`。  
  
```   
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    CTime& refValue,  
    const CTime* refMinRange,  
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,  
    COleDateTime& refValue,  
    const COleDateTime* refMinRange,  
    const COleDateTime* refMaxRange); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *refValue*  
 類型的物件參考`CTime`或`COleDateTime`對話方塊中的成員變數與相關聯，表單檢視，或控制項檢視物件。 此物件包含要驗證資料。 MFC 傳遞時參考這個`DDV_MinMaxMonth`呼叫。  
  
 `refMinRange`  
 最小日期/時間允許的值。  
  
 `refMaxRange`  
 允許的最大日期/時間值。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxshort"></a>DDV_MinMaxShort  
 呼叫`DDV_MinMaxShort`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,  
    short value,  
    short minVal,  
    short maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**簡短**) 允許。  
  
 `maxVal`  
 最大值 (類型的**簡短**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxslider"></a>DDV_MinMaxSlider  
 呼叫`DDV_MinMaxSlider`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,  
    DWORD value,  
    DWORD minVal,  
    DWORD maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 指標[CDataExchange](../../mfc/reference/cdataexchange-class.md)物件。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 要驗證值的參考。 這個參數會存放或設定滑桿控制項的目前捲動方塊位置。  
  
 `minVal`  
 允許的最小值。  
  
 `maxVal`  
 允許的最大值。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。 滑桿控制項的相關資訊，請參閱[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxuint"></a>DDV_MinMaxUInt  
 呼叫`DDV_MinMaxUInt`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,  
    UINT value,  
    UINT minVal,  
    UINT maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**UINT**) 允許。  
  
 `maxVal`  
 最大值 (類型的**UINT**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  
  
### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
  
##  <a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong  
 呼叫`DDV_MinMaxULongLong`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
  
```   
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,  
    ULONGLONG value,  
    ULONGLONG  minVal ,  
    ULONGLONG  maxVal); 
```  
  
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**ULONGLONG**) 允許。  
  
 `maxVal`  
 最大值 (類型的**ULONGLONG**) 允許。  
  
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)。  

### <a name="requirements"></a>需求  
  **標頭**afxdd_.h  
    
## <a name="see-also"></a>請參閱  
 [標準對話方塊資料交換常式](../../mfc/reference/standard-dialog-data-exchange-routines.md)   
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)

 ## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned
呼叫`DDV_MinMaxUnsigned`驗證控制項中的值聯*值*介於`minVal`和`maxVal`。  
   
### <a name="syntax"></a>語法    
```
   void AFXAPI DDV_MinMaxUnsigned(  
       CDataExchange* pDX,  
       unsigned value,  
       unsigned minVal,  
       unsigned maxVal );  
```
### <a name="parameters"></a>參數  
 `pDX`  
 `CDataExchange` 物件的指標。 架構會提供此物件來建立資料交換的內容，包括其方向。  
  
 *值*  
 對話方塊、 表單檢視中或用來驗證資料的控制項檢視物件的成員變數參考。  
  
 `minVal`  
 最小值 (類型的**不帶正負號**) 允許。  
  
 `maxVal`  
 最大值 (類型的**不帶正負號**) 允許。  
   
### <a name="remarks"></a>備註  
 如需 DDV 的詳細資訊，請參閱[對話方塊資料交換和驗證](../dialog-data-exchange-and-validation.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxdd_.h  
   
### <a name="see-also"></a>請參閱  
 [巨集和全域變數](mfc-macros-and-globals.md)   
 [DDX_Slider](#ddx_slider)   
 [DDX_FieldSlider](#ddx_fieldslider)
 


