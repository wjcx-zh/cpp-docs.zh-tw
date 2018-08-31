---
title: CFont 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2781a41ddadc6932e1c5797f098407b7dd5e4f29
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221224"
---
# <a name="cfont-class"></a>CFont 類別
封裝 Windows 繪圖裝置介面 (GDI) 字型並提供操作字型的成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|建構 `CFont` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|初始化`CFont`具有指定特性。|  
|[Cfont:: Createfontindirect](#createfontindirect)|初始化`CFont`物件中指定的特性`LOGFONT`結構。|  
|[CFont::CreatePointFont](#createpointfont)|初始化`CFont`與指定的高度，測量中的點，以及字樣的十分之一秒。|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|與相同`CreateFontIndirect`不同之處在於字型高度以一個點，而不是邏輯單元的十分之一秒。|  
|[CFont::FromHandle](#fromhandle)|將指標傳回至`CFont`物件時指定 Windows HFONT。|  
|[CFont::GetLogFont](#getlogfont)|填滿`LOGFONT`附加到的邏輯字型資訊`CFont`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CFont::operator HFONT](#operator_hfont)|傳回 Windows GDI 字型控制代碼附加至`CFont`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CFont`物件，建構`CFont`物件，並對其附加 Windows 字型[CreateFont](#createfont)， [CreateFontIndirect](#createfontindirect)， [CreatePointFont](#createpointfont)，或是[CreatePointFontIndirect](#createpointfontindirect)，然後使用物件的成員函式，來操作字型。  
  
 `CreatePointFont`並`CreatePointFontIndirect`函式通常是容易使用比`CreateFont`或`CreateFontIndirect`因為他們如何字型的高度的轉換，從點大小邏輯單元會自動。  
  
 如需詳細資訊`CFont`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cfont"></a>  CFont::CFont  
 建構 `CFont` 物件。  
  
```  
CFont();
```  
  
### <a name="remarks"></a>備註  
 產生的物件必須 nelze s položkami `CreateFont`， `CreateFontIndirect`， `CreatePointFont`，或`CreatePointFontIndirect`才可使用。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>  CFont::CreateFont  
 初始化`CFont`具有指定特性的物件。  
  
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
 *nHeight*  
 指定字型的所需的高度 （以邏輯單位表示）。 請參閱`lfHeight`隸屬[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構描述的 Windows SDK 中。 數值的絕對值*nHeight*不得超過 16,384 裝置單位之後則會轉換。 對於所有高度比較，字型對應工具會尋找最大的字型不會超過要求的大小或最小字型如果所有字型都超過要求的大小。  
  
 *nWidth*  
 指定字型中的字元平均寬度 （以邏輯單位表示）。 如果*nWidth*為 0 時，裝置的長寬比會比對可用的字型，尋找最接近的相符項目是由差異的絕對值決定數位化外觀比例。  
  
 *nEscapement*  
 指定字體斜度向量與顯示表面的 x 軸之間的角度 （以 0.1 度為單位）。 字體斜度向量是透過第一個和最後一個字元，在某一行的起源的線條。 從 x 軸逆時針測量的角度。 請參閱`lfEscapement`中的成員`LOGFONT`結構在 Windows SDK 中，如需詳細資訊。  
  
 *nOrientation*  
 指定字元的基準線與 x 軸之間的角度 （以 0.1 度為單位）。 角度是從 y 方向是向下和順時針自 x 軸，y 方向已啟動的座標系統的座標系統的 x 軸逆時針測量的。  
  
 *nWeight*  
 指定字型粗細 （以每 1000年個有著色的像素）。 請參閱*lfWeight*中的成員`LOGFONT`結構在 Windows SDK 中，如需詳細資訊。 描述的值為估計值;實際的外觀取決於字樣。 有些字型有只 FW_NORMAL，FW_REGULAR，FW_BOLD 的加權。 如果指定 FW_DONTCARE，則會使用預設權數。  
  
 *bItalic*  
 指定字型是否為斜體。  
  
 *bUnderline*  
 指定字型是否加上底線。  
  
 *cStrikeOut*  
 指定字型中的字元會被封殺出局。如果指定刪除線字型設定為非零值。  
  
 *nCharSet*  
 指定字型的字元 setSee`lfCharSet`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 OEM 字元集是系統而定。  
  
 使用其他字元集的字型可能存在於系統中。 未知的字元組使用字型的應用程式必須嘗試轉譯或解譯字串時，會利用該字型來進行轉譯。 相反地，字串應該直接傳遞給輸出裝置驅動程式。  
  
 字型對應工具不會使用 DEFAULT_CHARSET 值。 應用程式可以使用此值，以允許的名稱和完整描述的邏輯字型字型的大小。 具有指定名稱的字型不存在，如果指定的字型，可取代從任何字元集的字型。 若要避免非預期的結果，應用程式應該謹慎使用 DEFAULT_CHARSET 值。  
  
 *nOutPrecision*  
 指定所需的輸出有效位數。 輸出精確度會定義要求之的字型的高度、 寬度、 字元方向、 字體斜度和音調必須符合輸出的程度。 請參閱`lfOutPrecision`中的成員`LOGFONT`的值和更多的資訊清單的 Windows SDK 中的結構。  
  
 *nClipPrecision*  
 指定所要的裁剪精確值。 裁剪精確值會定義如何裁剪部分的裁剪區域以外的字元。 請參閱`lfClipPrecision`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 若要使用內嵌的唯讀字型，應用程式必須指定 CLIP_ENCAPSULATE。  
  
 若要達到一致的旋轉的裝置、 TrueType 和選取向量字型，應用程式可以使用 OR 運算子結合 CLIP_LH_ANGLES 值與任何其他*nClipPrecision*值。 如果設定的 CLIP_LH_ANGLES 位元，所有字型的旋轉取決於座標系統的方向是慣用左手或右手拿。 (如需詳細的座標系統方向的詳細資訊，請參閱的描述*nOrientation*參數。)如果未設定 CLIP_LH_ANGLES，裝置字型一律旋轉以逆時針方向，但其他字型的旋轉角度是座標系統的方向而定。  
  
 *nQuality*  
 指定字型的輸出品質，定義如何仔細 GDI 必須嘗試比對的實際實體字型的邏輯字型屬性。 請參閱`lfQuality`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 *nPitchAndFamily*  
 指定的字幅和家族的字型。 請參閱`lfPitchAndFamily`中的成員`LOGFONT`的值和更多的資訊清單的 Windows SDK 中的結構。  
  
 *lpszFacename*  
 A`CString`或以 null 終止的字串，指定字型的字樣名稱的指標。 這個字串的長度不能超過 30 個字元。 Windows [EnumFontFamilies](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesa)函式可用來列舉所有目前可用的字型。 如果*lpszFacename*是 NULL，GDI 會使用與裝置無關的字樣。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著可以為任何裝置內容的字型選取字型。  
  
 `CreateFont`函式不會建立新的 Windows GDI 字型。 只選取最接近的相符項目，從可用的實體字型 GDI。  
  
 應用程式可以使用預設設定，大部分的參數，建立邏輯字型時。 一律應該指定特定值的參數*nHeight*並*lpszFacename*。 如果*nHeight*並*lpszFacename*未設定應用程式，所建立的邏輯字型是裝置而異。  
  
 當您完成使用`CFont`所建立的物件`CreateFont`函式中，使用`CDC::SelectObject`若要選取不同的字型，放入裝置內容，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>  Cfont:: Createfontindirect  
 初始化`CFont`物件中指定的特性[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>參數  
 *lpLogFont*  
 指向`LOGFONT`結構，定義邏輯字型的特性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 後續可以為任何裝置的目前字型選取字型。  
  
 此字型已在指定的特性[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構。 使用選取的字型時[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)成員函式，GDI 字型對應工具會嘗試比對使用現有的實體字型的邏輯字型。 如果字型對應程式無法找到完全相符的邏輯字型，它會提供替代的字型，其特性符合多個要求的特性越好。  
  
 當您不再需要`CFont`所建立的物件`CreateFontIndirect`函式中，使用`CDC::SelectObject`若要選取不同的字型，放入裝置內容，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>  CFont::CreatePointFont  
 此函式會提供簡單的方式，建立指定的字樣的字型，並指向大小。  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 *nPointSize*  
 要求的字型高度，以資料點的十分之一秒。 （例如，傳遞要求 12 點字型 120。）  
  
 *lpszFaceName*  
 A`CString`或以 null 終止的字串，指定字型的字樣名稱的指標。 這個字串的長度不能超過 30 個字元。 Windows ' EnumFontFamilies 函式可用來列舉所有目前可用的字型。 如果*lpszFaceName*是 NULL，GDI 會使用與裝置無關的字樣。  
  
 *pDC*  
 指標[CDC](../../mfc/reference/cdc-class.md)物件，以用來轉換在高度*nPointSize*邏輯的單位。 如果是 NULL，螢幕裝置內容是用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 它會自動轉換在高度*nPointSize*邏輯的單位使用的 CDC 物件指向*pDC*。  
  
 當您完成使用`CFont`所建立的物件`CreatePointFont`函式，請先選取的字型，從裝置內容，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>  CFont::CreatePointFontIndirect  
 此函式是相同[CreateFontIndirect](#createfontindirect)只不過`lfHeight`的成員`LOGFONT`解譯中的點，而不是裝置單位的十分之一秒。  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 *lpLogFont*  
 指向[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)結構，定義邏輯字型的特性。 `lfHeight`隸屬`LOGFONT`結構以一個點，而不是邏輯單元的十分之一秒。 (例如，設定`lfHeight`為要求 12 點字型 120。)  
  
 *pDC*  
 指標[CDC](../../mfc/reference/cdc-class.md)物件，以用來轉換在高度`lfHeight`邏輯的單位。 如果是 NULL，螢幕裝置內容是用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會自動轉換在高度`lfHeight`邏輯的單位使用的 CDC 物件所指的*pDC*然後再傳遞`LOGFONT`入 Windows 的結構。  
  
 當您完成使用`CFont`所建立的物件`CreatePointFontIndirect`函式，請先選取的字型，從裝置內容，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>  CFont::FromHandle  
 將指標傳回至`CFont`物件時 HFONT 控制代碼給 Windows GDI 字型物件。  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>參數  
 *hFont*  
 Windows 字型 HFONT 控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CFont`如果成功，否則為 NULL 的物件。  
  
### <a name="remarks"></a>備註  
 如果`CFont`物件尚未附加至控制代碼，暫存`CFont`建立物件並將其連結。 此暫存`CFont`物件是否有效，直到下一次應用程式在其事件迴圈中有閒置的時間，在那所有暫存的圖形物件，會刪除只。 另一種說法是暫存的物件有效，只在一個視窗訊息的處理。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>  CFont::GetLogFont  
 呼叫此函式可擷取一份`LOGFONT`結構`CFont`。  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>參數  
 *pLogFont*  
 指標[LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta)接收的字型資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，則為 0，非零值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>  CFont::operator HFONT  
 使用這個運算子來取得 Windows GDI 控制代碼，附加至的字型`CFont`物件。  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows GDI 字型物件的控制代碼附加至`CFont`如果成功，否則為 NULL。  
  
### <a name="remarks"></a>備註  
 因為這個運算子會自動用於從不`CFont`要[字型和文字](/windows/desktop/gdi/fonts-and-text)，您可以傳遞`CFont`HFONTs 函式的物件。  
  
 如需使用 圖形物件的詳細資訊，請參閱 <<c0> [ 圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



