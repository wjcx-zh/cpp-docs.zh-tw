---
title: "CFont 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
dev_langs:
- C++
helpviewer_keywords:
- CFont class
- GDI, font classes
- fonts, MFC classes
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cc7ecfb850bf24013acdb55075eeb3d64d4994ee
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cfont-class"></a>CFont 類別
封裝 Windows 繪圖裝置介面 (GDI) 字型並提供操作字型的成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|建構 `CFont` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|初始化`CFont`具指定特性。|  
|[Cfont:: Createfontindirect](#createfontindirect)|初始化`CFont`物件中指定的特性`LOGFONT`結構。|  
|[CFont::CreatePointFont](#createpointfont)|初始化`CFont`與指定的高度，以點，以及字樣的十分之一。|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|相同`CreateFontIndirect`不同之處在於字型高度以點，而不是邏輯單位的十分之一。|  
|[CFont::FromHandle](#fromhandle)|傳回的指標`CFont`物件時指定 Windows **HFONT**。|  
|[CFont::GetLogFont](#getlogfont)|填滿`LOGFONT`附加到的邏輯字型資訊`CFont`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|Windows GDI 字型控制代碼會附加至傳回`CFont`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CFont`物件，建構`CFont`物件，並附加於其使用的 Windows 字型[CreateFont](#createfont)， [CreateFontIndirect](#createfontindirect)， [CreatePointFont](#createpointfont)，或[CreatePointFontIndirect](#createpointfontindirect)，然後使用物件的成員函式來操作字型。  
  
 `CreatePointFont`和`CreatePointFontIndirect`函式通常會比`CreateFont`或`CreateFontIndirect`因為他們如何字型高度的轉換，從點大小邏輯單元自動。  
  
 如需有關`CFont`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cfont"></a>CFont::CFont  
 建構 `CFont` 物件。  
  
```  
CFont();
```  
  
### <a name="remarks"></a>備註  
 產生的物件必須以初始化`CreateFont`， `CreateFontIndirect`， `CreatePointFont`，或`CreatePointFontIndirect`才可使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&70;](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>CFont::CreateFont  
 初始化`CFont`具指定特性的物件。  
  
```  
BOOL CreateFont(
    int nHeight,  
    int nWidth,  
    int nEscapement,  
    int nOrientation,  
    int nWeight,  
    BYTE bItalic,  
    BYTE bUnderline,  
    BYTE cStrikeOut,  
    BYTE nCharSet,  
    BYTE nOutPrecision,  
    BYTE nClipPrecision,  
    BYTE nQuality,  
    BYTE nPitchAndFamily,  
    LPCTSTR lpszFacename);
```  
  
### <a name="parameters"></a>參數  
 `nHeight`  
 指定所需的字型的高度 （以邏輯單位表示）。 請參閱`lfHeight`成員[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的描述。 數值的絕對值`nHeight`」 轉換後不能超過 16384 裝置單位。 所有高度比較，字型對應工具不會超過所要求的大小的最大字型或最小的字型看都起來的所有字型都超過所要求的大小。  
  
 `nWidth`  
 指定字型中的平均字元寬度 （以邏輯單位表示）。 如果`nWidth`是 0，則裝置的外觀比例會比對可用的字型，尋找最接近的相符項目取決於差異的絕對值數位化外觀比例。  
  
 `nEscapement`  
 指定斜度向量與顯示表面的 x 軸的角度 （以 0.1 度為單位）。 斜度向量是透過在一行的第一個和最後一個字元的原始來源。 角度是以逆時針方向測量之從 x 軸。 請參閱`lfEscapement`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
 `nOrientation`  
 指定字元的基準線與 x 軸的角度 （以 0.1 度為單位）。 角度是以逆時針方向測量之從 x 軸，y 方向是向下和從 y 方向已啟動的座標系統的 x 軸順時針的座標系統。  
  
 `nWeight`  
 指定字型粗細 （以每 1000年有著色的像素）。 請參閱`lfWeight`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。 描述的值是近似值;實際的外觀取決於字樣。 有些字型僅具有`FW_NORMAL`， `FW_REGULAR`，和`FW_BOLD`加權。 如果`FW_DONTCARE`指定，則使用預設權數。  
  
 `bItalic`  
 指定字型是否為斜體。  
  
 `bUnderline`  
 指定字型是否加上底線。  
  
 `cStrikeOut`  
 指定字型中的字元是否會被封殺出局。 如果指定刪除線字型設定為非零值。  
  
 `nCharSet`  
 指定字型的字元 setSee`lfCharSet`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
 OEM 字元集與系統相關。  
  
 與其他字元集的字型可能存在於系統中。 使用未知的字元集的字型的應用程式必須嘗試轉換或解譯字串時，會利用該字型來進行轉譯。 相反地，字串應該直接傳遞給輸出裝置驅動程式。  
  
 字型對應工具不會使用`DEFAULT_CHARSET`值。 應用程式可以使用這個值允許的名稱和完整描述的邏輯字型的字型的大小。 如果具有指定名稱的字型不存在，可以指定字型取代任何字元集的字型。 若要避免非預期的結果，應用程式應使用`DEFAULT_CHARSET`盡量少用值。  
  
 `nOutPrecision`  
 指定想要的輸出有效位數。 輸出精確度可定義要求的字型高度、 寬度、 字元方向、 斜度和音調必須符合輸出的程度。 請參閱`lfOutPrecision`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的值清單和詳細資訊。  
  
 `nClipPrecision`  
 指定所要的裁剪的有效位數。 裁剪精確值會定義如何裁剪部分裁剪區域外的字元。 請參閱`lfClipPrecision`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
 若要使用內嵌的唯讀字型，應用程式必須指定`CLIP_ENCAPSULATE`。  
  
 若要達成一致旋轉的裝置、 細明體和向量字型，應用程式可以使用 OR 運算子結合`CLIP_LH_ANGLES`值與任何其他`nClipPrecision`值。 如果`CLIP_LH_ANGLES`位元會設、 所有字型旋轉，取決於座標系統的方向是慣用左手或右手拿筆。 (如需方向的座標系統的詳細資訊，請參閱的描述`nOrientation`參數。)如果`CLIP_LH_ANGLES`是未設定，裝置字型一律旋轉以逆時針方向，但其他字型的旋轉角度是座標系統的方向而定。  
  
 `nQuality`  
 指定字型的輸出品質定義小心 GDI 必須嘗試比對的實際實體字型的邏輯字型屬性。 請參閱`lfQuality`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
 `nPitchAndFamily`  
 指定的頻率和字型系列。 請參閱`lfPitchAndFamily`中的成員`LOGFONT`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的值清單和詳細資訊。  
  
 `lpszFacename`  
 A`CString`或以 null 終止的字串，指定字型的字樣名稱的指標。 這個字串的長度不得超過 30 個字元。 Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619)函式可用來列舉所有目前可用的字型。 如果`lpszFacename`是`NULL`，GDI 會使用與裝置無關的字樣。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為任何裝置內容的字型選取字型。  
  
 `CreateFont`函式不會建立新的 Windows GDI 字型。 只選取最接近的相符項目，從可用的實體字型 GDI。  
  
 應用程式的預設設定用於大多數參數建立時可以使用邏輯字型。 應該一律對具有特定值的參數是`nHeight`和`lpszFacename`。 如果`nHeight`和`lpszFacename`未設定應用程式建立的邏輯字型會因裝置而異。  
  
 當您完成使用`CFont`所建立物件`CreateFont`函式，請使用`CDC::SelectObject`放入裝置內容中選取不同的字型，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&71;](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>Cfont:: Createfontindirect  
 初始化`CFont`物件中指定的特性[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>參數  
 `lpLogFont`  
 指向`LOGFONT`結構，定義邏輯字型的特性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為任何裝置的目前字型選取字型。  
  
 此字型已在指定的特性[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。 使用選取的字型時[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)成員函式，GDI 字型對應工具會嘗試使用現有的實體字型的邏輯字型。 如果字型對應器找不到相符的邏輯字型，它會提供其特性符合最大數量的要求特性替代字型。  
  
 當您不再需要`CFont`所建立物件`CreateFontIndirect`函式，請使用`CDC::SelectObject`放入裝置內容中選取不同的字型，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&72;](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>CFont::CreatePointFont  
 此函數會提供簡單的方式來建立指定之字型的字型和點數大小。  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nPointSize`  
 要求的字型高度，單位為點的十分之一。 （比方說，傳遞要求 12 點字型 120）。  
  
 `lpszFaceName`  
 A`CString`或以 null 終止的字串，指定字型的字樣名稱的指標。 這個字串的長度不得超過 30 個字元。 Windows **EnumFontFamilies**函式可用來列舉所有目前可用的字型。 如果`lpszFaceName`是**NULL**，GDI 會使用與裝置無關的字樣。  
  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件用來轉換在高度`nPointSize`邏輯單位。 如果**NULL**，螢幕裝置內容用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 它會自動將轉換的高度以`nPointSize`要使用的邏輯單元`CDC`指向的物件`pDC`。  
  
 當您完成使用`CFont`所建立物件`CreatePointFont`函式，第一次選取的字型，從裝置內容，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&73;](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 此函式是相同[CreateFontIndirect](#createfontindirect)不同之處在於**lfHeight**成員`LOGFONT`解譯中的點，而不是裝置單位的十分之一。  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpLogFont`  
 指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構，定義邏輯字型的特性。 **LfHeight**成員`LOGFONT`結構的測量單位是點，而不是邏輯單位的十分之一。 (例如，設定**lfHeight**為要求 12 點字型 120。)  
  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件用來轉換在高度**lfHeight**邏輯單位。 如果**NULL**，螢幕裝置內容用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會自動將轉換的高度以**lfHeight**要使用的邏輯單元`CDC`指向的物件`pDC`傳遞之前`LOGFONT`到 Windows 的結構。  
  
 當您完成使用`CFont`所建立物件`CreatePointFontIndirect`函式，第一次選取的字型，從裝置內容，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&74;](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CFont::FromHandle  
 傳回的指標`CFont`物件時指定**HFONT** Windows GDI 字型物件控制代碼。  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>參數  
 `hFont`  
 **HFONT** Windows 字型的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CFont`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CFont`物件尚未附加至控制代碼，暫存`CFont`會建立並附加物件。 此暫存`CFont`僅直到下一次應用程式在其事件迴圈中有閒置時間，在這次所有暫存圖形會刪除物件，物件才有效。 另一種說法是暫存物件只在一個視窗訊息處理期間會有效。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&75;](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>CFont::GetLogFont  
 呼叫此函式可擷取一份`LOGFONT`結構`CFont`。  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>參數  
 *pLogFont*  
 指標[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)接收字型資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，否則為 0，非零值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&76;](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>CFont::operator HFONT  
 若要取得 Windows GDI 字型的控制代碼附加至使用此運算子`CFont`物件。  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows GDI 字型物件的控制代碼會附加至`CFont`如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 因為這個運算子會自動用於從不`CFont`至[字型和文字](http://msdn.microsoft.com/library/windows/desktop/dd144819)，您可以傳遞`CFont`預期的函式物件**HFONT**s。  
  
 如需使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&77;](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)




