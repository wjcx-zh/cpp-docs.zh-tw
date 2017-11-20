---
title: "CFont 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65c1fd6d86c153881f8674732db2b61edcfab8cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cfont-class"></a>CFont 類別
封裝 Windows 繪圖裝置介面 (GDI) 字型並提供操作字型的成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CFont : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CFont::CFont](#cfont)|建構 `CFont` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFont::CreateFont](#createfont)|初始化`CFont`與指定的特性。|  
|[Cfont:: Createfontindirect](#createfontindirect)|初始化`CFont`物件中指定的特性`LOGFONT`結構。|  
|[CFont::CreatePointFont](#createpointfont)|初始化`CFont`與指定的高度，以點，以及字樣的十分之一。|  
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|與相同`CreateFontIndirect`不同之處在於字型高度以點，而不是邏輯單元的十分之一。|  
|[CFont::FromHandle](#fromhandle)|將指標傳回至`CFont`物件時指定 Windows **HFONT**。|  
|[CFont::GetLogFont](#getlogfont)|填滿`LOGFONT`附加到的邏輯字型相關資訊`CFont`物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[HFONT CFont::operator](#operator_hfont)|傳回 Windows GDI 字型控制代碼附加至`CFont`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CFont`物件，然後建構`CFont`物件，並附加至與 Windows 字型[CreateFont](#createfont)， [CreateFontIndirect](#createfontindirect)， [CreatePointFont](#createpointfont)，或[CreatePointFontIndirect](#createpointfontindirect)，然後使用物件的成員函式來操作字型。  
  
 `CreatePointFont`和`CreatePointFontIndirect`函式通常是容易使用比`CreateFont`或`CreateFontIndirect`因為它們自動執行作業的字型高度的轉換，從點大小到邏輯單元。  
  
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
 產生的物件必須初始化與`CreateFont`， `CreateFontIndirect`， `CreatePointFont`，或`CreatePointFontIndirect`才能使用它。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]  
  
##  <a name="createfont"></a>CFont::CreateFont  
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
 `nHeight`  
 指定字型的所需的高度 （以邏輯單位表示）。 請參閱`lfHeight`隸屬[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構描述的 Windows SDK 中。 數值的絕對值`nHeight`之後會將它轉換，則不能超過 16,384 裝置單位。 對於所有高度比較，字型對應工具會尋找所要求的大小不超過最大字型或最小字型如果所有字型都超過要求的大小。  
  
 `nWidth`  
 指定字型中的平均字元寬度 （以邏輯單位表示）。 如果`nWidth`為 0 時，裝置的外觀比例會比對可用的字型，尋找最接近的相符項目是由差異的絕對值決定 digitization 外觀比例。  
  
 `nEscapement`  
 指定之間斜度向量與顯示表面的 x 軸的角度 （以 0.1 度為單位）。 斜度向量是該行的第一個和最後一個字元的出處線。 從 x 軸逆時針計算角度。 請參閱`lfEscapement`中的成員`LOGFONT`結構的詳細資訊的 Windows SDK 中。  
  
 `nOrientation`  
 指定字元的基準線與 x 軸之間的角度 （以 0.1 度為單位）。 從 y 方向是向下和順時針方向從 x 軸座標系統 y 方向已啟動的座標系統的 x 軸逆時針計算角度。  
  
 `nWeight`  
 指定字型粗細 （以每 1000年有著色的像素）。 請參閱`lfWeight`中的成員`LOGFONT`結構的詳細資訊的 Windows SDK 中。 描述的值是近似值;實際的外觀取決於字樣。 有些字型只有`FW_NORMAL`， `FW_REGULAR`，和`FW_BOLD`加權。 如果`FW_DONTCARE`已指定，會使用預設權數。  
  
 `bItalic`  
 指定字型是否為斜體。  
  
 `bUnderline`  
 指定字型是否加上底線。  
  
 `cStrikeOut`  
 指定字型中的字元是否為侵襲。指定刪除線的字型，如果設定為非零值。  
  
 `nCharSet`  
 指定字型的字元 setSee`lfCharSet`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 OEM 字元集是系統而定。  
  
 與其他字元集的字型可能存在於系統中。 使用未知的字元集的字型的應用程式必須嘗試將轉譯或解譯字串時，會為要轉換成該字型。 相反地，字串應該直接傳遞至輸出裝置驅動程式。  
  
 未使用的字型對應程式`DEFAULT_CHARSET`值。 應用程式可以使用此值，以允許的名稱和完整描述的邏輯字型的字型的大小。 如果具有指定名稱的字型不存在，可以指定字型取代任何字元集中的字型。 若要避免非預期的結果，應用程式應該使用`DEFAULT_CHARSET`盡量少用值。  
  
 `nOutPrecision`  
 指定想要的輸出有效位數。 輸出精確度定義所要求的字型高度、 寬度、 字元方向、 斜度及字距必須符合輸出的程度。 請參閱`lfOutPrecision`中的成員`LOGFONT`一份值的詳細資訊的 Windows SDK 中的結構。  
  
 `nClipPrecision`  
 指定所要的裁剪的有效位數。 裁剪有效位數會定義如何裁剪部分裁剪區域外的字元。 請參閱`lfClipPrecision`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 若要使用內嵌的唯讀字型，應用程式必須指定`CLIP_ENCAPSULATE`。  
  
 若要達到一致的裝置、 細明體和向量字型的旋轉角度，應用程式可以使用 OR 運算子結合`CLIP_LH_ANGLES`值與任何其他`nClipPrecision`值。 如果`CLIP_LH_ANGLES`會設定位元、 所有字型的旋轉角度取決於座標系統的方向是慣用左手或右手拿。 (如需座標系統的方向的詳細資訊，請參閱描述`nOrientation`參數。)如果`CLIP_LH_ANGLES`是未設定，裝置字型一律旋轉以逆時針方向，但其他字型輪替是依存於座標系統的方向。  
  
 `nQuality`  
 指定字型的輸出品質定義小心 GDI 必須嘗試比對的實際實體字型的邏輯字型屬性。 請參閱`lfQuality`中的成員`LOGFONT`值清單的 Windows SDK 中的結構。  
  
 `nPitchAndFamily`  
 指定的字幅和家族的字型。 請參閱`lfPitchAndFamily`中的成員`LOGFONT`一份值的詳細資訊的 Windows SDK 中的結構。  
  
 `lpszFacename`  
 A`CString`或以 null 終止的字串，指定之字型的字體名稱的指標。 這個字串的長度不能超過 30 個字元。 Windows [EnumFontFamilies](http://msdn.microsoft.com/library/windows/desktop/dd162619)函式可以用來列舉所有目前可用的字型。 如果`lpszFacename`是`NULL`，GDI 使用裝置獨立字樣。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接下來可以做為任何裝置內容的字型為選取的字型。  
  
 `CreateFont`函式不會建立新的 Windows GDI 字型。 只選取最接近的相符項目，從可用的實體字型 GDI。  
  
 應用程式可以使用預設設定大部分的參數建立的邏輯字型時。 應該永遠指定特定值的參數是`nHeight`和`lpszFacename`。 如果`nHeight`和`lpszFacename`未設定應用程式，所建立的邏輯字型是裝置而異。  
  
 當您完成使用`CFont`所建立的物件`CreateFont`函式，使用`CDC::SelectObject`放入裝置內容中選取不同的字型，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]  
  
##  <a name="createfontindirect"></a>Cfont:: Createfontindirect  
 初始化`CFont`物件中指定的特性[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。  
  
```  
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```  
  
### <a name="parameters"></a>參數  
 `lpLogFont`  
 指向`LOGFONT`結構，定義的邏輯字型的特性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接下來可以為任何裝置的目前字型選取的字型。  
  
 此字型已在指定的特性[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構。 使用選取的字型是當[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)成員函式，GDI 字型對應工具會嘗試比對以現有的實體字型的邏輯字型。 如果字型對應程式找不到完全相符的邏輯字型，它會提供替代的字型，其特性符合最大數量的要求特性。  
  
 當您不再需要`CFont`所建立的物件`CreateFontIndirect`函式，使用`CDC::SelectObject`放入裝置內容中選取不同的字型，然後刪除`CFont`不再需要的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]  
  
##  <a name="createpointfont"></a>CFont::CreatePointFont  
 此函式提供簡單的方法來建立指定字型的字型，以及點大小。  
  
```  
BOOL CreatePointFont(
    int nPointSize,  
    LPCTSTR lpszFaceName,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nPointSize`  
 要求的字型高度，單位為點的十分之一。 （例如，傳遞要求 12 點字型 120。）  
  
 `lpszFaceName`  
 A`CString`或以 null 終止的字串，指定之字型的字體名稱的指標。 這個字串的長度不能超過 30 個字元。 Windows **EnumFontFamilies**函式可以用來列舉所有目前可用的字型。 如果`lpszFaceName`是**NULL**，GDI 使用裝置獨立字樣。  
  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件用來將轉換的高度以`nPointSize`到邏輯單元。 如果**NULL**，螢幕裝置內容用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 它會自動將轉換的高度以`nPointSize`到使用邏輯單元`CDC`指向的物件`pDC`。  
  
 當您完成使用`CFont`所建立的物件`CreatePointFont`函式，請先選取的字型出裝置內容中，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]  
  
##  <a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect  
 此函式是相同[CreateFontIndirect](#createfontindirect)不同之處在於**lfHeight**隸屬`LOGFONT`解譯中的點，而不是裝置單位的十分之一。  
  
```  
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,  
    CDC* pDC = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpLogFont`  
 指向[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)結構，定義的邏輯字型的特性。 **LfHeight**隸屬`LOGFONT`結構為測量單位是點，而不是邏輯單元的十分之一。 (例如，設定**lfHeight**為要求 12 點字型 120。)  
  
 `pDC`  
 指標[CDC](../../mfc/reference/cdc-class.md)物件用來將轉換的高度以**lfHeight**到邏輯單元。 如果**NULL**，螢幕裝置內容用來進行轉換。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會自動將轉換的高度以**lfHeight**到使用邏輯單元`CDC`指向的物件`pDC`傳遞之前`LOGFONT`到 Windows 的結構。  
  
 當您完成使用`CFont`所建立的物件`CreatePointFontIndirect`函式，請先選取的字型出裝置內容中，然後刪除`CFont`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]  
  
##  <a name="fromhandle"></a>CFont::FromHandle  
 將指標傳回至`CFont`物件時指定**HFONT** Windows GDI 字型物件控制代碼。  
  
```  
static CFont* PASCAL FromHandle(HFONT hFont);
```  
  
### <a name="parameters"></a>參數  
 `hFont`  
 **HFONT** Windows 字型的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CFont`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CFont`物件未附加至控制代碼，暫存`CFont`物件會建立並附加。 此暫存`CFont`僅直到下一次應用程式有其事件迴圈中的閒置時間，在這次所有暫存圖形已刪除物件，物件才有效。 另一種說法是暫存物件是有效，只在一個視窗訊息的處理。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]  
  
##  <a name="getlogfont"></a>CFont::GetLogFont  
 呼叫此函式可擷取一份`LOGFONT`結構`CFont`。  
  
```  
int GetLogFont(LOGFONT* pLogFont);
```  
  
### <a name="parameters"></a>參數  
 *pLogFont*  
 指標[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)接收字型資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 非零，如果函式成功，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]  
  
##  <a name="operator_hfont"></a>HFONT CFont::operator  
 使用此運算子來取得 Windows GDI 控制代碼附加至的字型`CFont`物件。  
  
```  
operator HFONT() const;  
```  
  
### <a name="return-value"></a>傳回值  
 Windows GDI 字型物件控制代碼附加至`CFont`如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 因為這個運算子會自動用於從不`CFont`至[字型和文字](http://msdn.microsoft.com/library/windows/desktop/dd144819)，您可以傳遞`CFont`預期的函式物件**HFONT**s。  
  
 如需有關使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)



