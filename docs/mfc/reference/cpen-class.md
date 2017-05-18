---
title: "CPen 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
dev_langs:
- C++
helpviewer_keywords:
- HPEN
- CPen class
- pens, MFC
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
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
ms.openlocfilehash: edea12c84a8f39161acbf367360fd86a1ff19998
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cpen-class"></a>CPen 類別
封裝 Windows 繪圖裝置介面 (GDI) 畫筆。  
  
## <a name="syntax"></a>語法  
  
```  
class CPen : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPen::CPen](#cpen)|建構 `CPen` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CPen::CreatePen](#createpen)|使用指定的樣式、 寬度和筆刷屬性，建立邏輯表面或幾何畫筆，並附加至該`CPen`物件。|  
|[CPen::CreatePenIndirect](#createpenindirect)|建立畫筆與樣式、 寬度和色彩提供[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)結構，然後將它附加`CPen`物件。|  
|[CPen::FromHandle](#fromhandle)|傳回的指標`CPen`物件時指定 Windows `HPEN`。|  
|[CPen::GetExtLogPen](#getextlogpen)|取得[EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)基礎結構。|  
|[CPen::GetLogPen](#getlogpen)|取得[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)基礎結構。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CPen::operator HPEN](#operator_hpen)|連接至 Windows 控制代碼傳回`CPen`物件。|  
  
## <a name="remarks"></a>備註  
 如需有關使用`CPen`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cpen"></a>CPen::CPen  
 建構 `CPen` 物件。  
  
```  
CPen();

 
CPen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
CPen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nPenStyle`  
 指定的畫筆樣式。 建構函式的第一個版本中的這個參數可以是下列值之一︰  
  
- **PS_SOLID**建立穩固的畫筆。  
  
- **PS_DASH**建立虛線的畫筆。 畫筆寬度為 1 或更短，裝置中的單位時，才有效。  
  
- **PS_DOT**建立十進位的畫筆。 畫筆寬度為 1 或更短，裝置中的單位時，才有效。  
  
- **PS_DASHDOT**建立畫筆交替的虛線和點。 畫筆寬度為 1 或更短，裝置中的單位時，才有效。  
  
- **PS_DASHDOTDOT**交替的虛線和雙點建立畫筆。 畫筆寬度為 1 或更短，裝置中的單位時，才有效。  
  
- **PS_NULL**建立 null 畫筆。  
  
- **PS_INSIDEFRAME**建立畫筆繪製線條，以指定的周框矩形 Windows GDI 輸出函式所產生的封閉圖形的框架內，(比方說，**橢圓形**，**矩形**， `RoundRect`， `Pie`，和`Chord`成員函式)。 這個樣式搭配時未指定的周框矩形 Windows GDI 輸出函式 (例如，`LineTo`成員函式)，畫筆的繪圖區域不受限於的外框。  
  
 第二版`CPen`建構函式指定的型別、 樣式、 結束端點和聯結屬性組合。 使用位元 OR 運算子 (|)，應該結合每個類別目錄中的值。 畫筆類型可以是下列值之一︰  
  
- **PS_GEOMETRIC**建立幾何的畫筆。  
  
- **PS_COSMETIC**建立表面的畫筆。  
  
     第二版`CPen`建構函式加入下列畫筆樣式`nPenStyle`:  
  
- **PS_ALTERNATE**建立畫筆設定每個像素。 （這個樣式是只適用於表面畫筆）。  
  
- **PS_USERSTYLE**建立畫筆使用的使用者所提供的樣式陣列。  
  
     結束端點可以是下列值之一︰  
  
- **PS_ENDCAP_ROUND**端點會四捨五入。  
  
- **PS_ENDCAP_SQUARE**端點是正方形。  
  
- **PS_ENDCAP_FLAT**端點是平面。  
  
     聯結可以是下列值之一︰  
  
- **PS_JOIN_BEVEL**斜角聯結。  
  
- **PS_JOIN_MITER**聯結是斜接在目前所設定的限制範圍內時[SetMiterLimit](http://msdn.microsoft.com/library/windows/desktop/dd145076)函式。 如果聯結超過此限制，它被斜角。  
  
- **PS_JOIN_ROUND**聯結會四捨五入。  
  
 `nWidth`  
 指定將畫筆的寬度。  
  
-   建構函式的第一個版本，如果此值為 0，寬度裝置單位一律是 1 個像素，不論對應模式為何。  
  
-   第二個版本的建構函式，如果`nPenStyle`是**PS_GEOMETRIC**，以邏輯單位指定寬度。 如果`nPenStyle`是**PS_COSMETIC**，寬度必須設定為 1。  
  
 `crColor`  
 包含畫筆的 RGB 色彩。  
  
 `pLogBrush`  
 指向`LOGBRUSH`結構。 如果`nPenStyle`是**PS_COSMETIC**、`lbColor`成員`LOGBRUSH`結構指定的畫筆色彩和`lbStyle`成員`LOGBRUSH`結構必須設為**BS_SOLID**。 如果`nPenStyle`是**PS_GEOMETRIC**，所有成員必須都用來指定畫筆的筆刷屬性。  
  
 `nStyleCount`  
 指定的長度，單位 doubleword`lpStyle`陣列。 此值必須是零`nPenStyle`不**PS_USERSTYLE**。  
  
 `lpStyle`  
 Doubleword 值的陣列指標。 第一個值指定使用者定義的樣式中的第一條虛線的長度，第二個值指定長度的第一個空格，依此類推。 此指標必須在**NULL**如果`nPenStyle`不**PS_USERSTYLE**。  
  
### <a name="remarks"></a>備註  
 如果您使用不含引數的建構函式，您必須先初始化所產生的`CPen`物件`CreatePen`， `CreatePenIndirect`，或`CreateStockObject`成員函式。  
  
 如果您使用引數的建構函式時，沒有進一步的初始化是必要的。 如果發生錯誤，而不使用引數的建構函式一定會成功，則引數的建構函式可以擲回例外狀況。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&99;](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]  
  
##  <a name="createpen"></a>CPen::CreatePen  
 使用指定的樣式、 寬度和筆刷屬性，建立邏輯表面或幾何畫筆，並附加至該`CPen`物件。  
  
```  
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    COLORREF crColor);

 
BOOL CreatePen(
    int nPenStyle,  
    int nWidth,  
    const LOGBRUSH* pLogBrush,  
    int nStyleCount = 0,  
    const DWORD* lpStyle = NULL);
```  
  
### <a name="parameters"></a>參數  
 `nPenStyle`  
 指定的樣式的畫筆。 如需可能的值，請參閱`nPenStyle`中的參數[CPen](#cpen)建構函式。  
  
 `nWidth`  
 指定將畫筆的寬度。  
  
-   第一個版本的`CreatePen`，如果此值為 0，以裝置為單位的寬度一律為 1 個像素，不論對應模式為何。  
  
-   第二個版本的`CreatePen`，如果`nPenStyle`是**PS_GEOMETRIC**，以邏輯單位指定寬度。 如果`nPenStyle`是**PS_COSMETIC**，寬度必須設定為 1。  
  
 `crColor`  
 包含畫筆的 RGB 色彩。  
  
 `pLogBrush`  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。 如果`nPenStyle`是**PS_COSMETIC**、 **lbColor**成員`LOGBRUSH`結構指定的畫筆色彩和`lbStyle`成員`LOGBRUSH`結構必須設為**BS_SOLID**。 如果**nPenStyle**是**PS_GEOMETRIC**，所有成員必須都用來指定畫筆的筆刷屬性。  
  
 `nStyleCount`  
 指定的長度，單位 doubleword`lpStyle`陣列。 此值必須是零`nPenStyle`不**PS_USERSTYLE**。  
  
 `lpStyle`  
 Doubleword 值的陣列指標。 第一個值指定使用者定義的樣式中的第一條虛線的長度，第二個值指定長度的第一個空格，依此類推。 此指標必須在**NULL**如果`nPenStyle`不**PS_USERSTYLE**。  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，非零值或零，如果方法失敗。  
  
### <a name="remarks"></a>備註  
 第一版`CreatePen`初始化具有指定的樣式、 寬度和色彩的畫筆。 畫筆可以接著選取作為適用於任何裝置的內容目前的畫筆。  
  
 具有 1 個像素都應該有任何大於寬度的畫筆**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**樣式。  
  
 如果畫筆有**PS_INSIDEFRAME**樣式和色彩的不相符的邏輯色彩表，以遞色色彩繪製畫筆。 **PS_SOLID**畫筆樣式無法用來建立與遞色畫筆。 樣式**PS_INSIDEFRAME**等同於**PS_SOLID**畫筆寬度是否小於或等於 1。  
  
 第二版`CreatePen`初始化邏輯的表面或幾何畫筆具有指定樣式、 寬度和筆刷屬性。 表面畫筆的寬度永遠為 1。以全局單位一律指定幾何畫筆的寬度。 應用程式建立邏輯畫筆之後，它可以藉由呼叫放入裝置內容中選取該畫筆[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函式。 畫筆選入裝置內容之後，它可用來繪製的直線和曲線。  
  
-   如果`nPenStyle`是**PS_COSMETIC**和**PS_USERSTYLE**中的項目`lpStyle`陣列指定虛線和間距的長度，單位為樣式。 樣式單元會定義其中畫筆會繪製一條線使用的裝置。  
  
-   如果`nPenStyle`是**PS_GEOMETRIC**和**PS_USERSTYLE**中的項目`lpStyle`陣列指定虛線和間距的長度，以邏輯單位表示。  
  
-   如果`nPenStyle`是**PS_ALTERNATE**、 樣式單位會被忽略，而且設定每個像素。  
  
 當應用程式不再需要指定的畫筆時，它應該呼叫[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式或損毀`CPen`物件，以便資源不再使用。 在裝置內容中選取畫筆時，應用程式不應該刪除畫筆。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&100;](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]  
  
##  <a name="createpenindirect"></a>CPen::CreatePenIndirect  
 初始化具有樣式、 寬度和色彩所指向的結構所提供的畫筆`lpLogPen`。  
  
```  
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```  
  
### <a name="parameters"></a>參數  
 `lpLogPen`  
 Windows 會指向[LOGPEN](../../mfc/reference/logpen-structure.md)包含畫筆的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 具有 1 個像素都應該有任何大於寬度的畫筆**PS_NULL**， **PS_SOLID**，或**PS_INSIDEFRAME**樣式。  
  
 如果畫筆有**PS_INSIDEFRAME**樣式和色彩的不相符的邏輯色彩表，以遞色色彩繪製畫筆。 **PS_INSIDEFRAME**樣式等同於**PS_SOLID**畫筆寬度是否小於或等於 1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&101;](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]  
  
##  <a name="fromhandle"></a>CPen::FromHandle  
 傳回的指標`CPen`給 Windows GDI pen 物件控制代碼的物件。  
  
```  
static CPen* PASCAL FromHandle(HPEN hPen);
```  
  
### <a name="parameters"></a>參數  
 *hPen*  
 `HPEN`Windows GDI 畫筆的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CPen`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果 `CPen` 物件沒有附加至控制代碼，會建立並附加暫存 `CPen` 物件。 此暫存`CPen`僅直到下一次應用程式在其事件迴圈中有閒置時間，在這次所有暫存圖形會刪除物件，物件才有效。 換句話說，此暫存物件只適用於一個視窗訊息處理期間。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&105;](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]  
  
##  <a name="getextlogpen"></a>CPen::GetExtLogPen  
 取得**EXTLOGPEN**基礎結構。  
  
```  
int GetExtLogPen(EXTLOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>參數  
 `pLogPen`  
 指向[EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)包含畫筆的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 **EXTLOGPEN**結構會定義樣式、 寬度和畫筆的筆刷屬性。 例如，呼叫`GetExtLogPen`以符合特定樣式的畫筆。  
  
 請參閱下列主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的畫筆屬性的相關資訊︰  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
- [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)  
  
### <a name="example"></a>範例  
 下列程式碼範例示範如何呼叫`GetExtLogPen`擷取手寫筆的屬性，並再建立新的表面畫筆使用相同的色彩。  
  
 [!code-cpp[NVC_MFCDocView #&102;](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]  
  
##  <a name="getlogpen"></a>CPen::GetLogPen  
 取得`LOGPEN`基礎結構。  
  
```  
int GetLogPen(LOGPEN* pLogPen);
```  
  
### <a name="parameters"></a>參數  
 `pLogPen`  
 指向[LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)結構以包含畫筆的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `LOGPEN`結構會定義樣式、 色彩和畫筆的模式。  
  
 例如，呼叫`GetLogPen`以符合特定樣式的畫筆。  
  
 請參閱下列主題[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的畫筆屬性的相關資訊︰  
  
- [GetObject](http://msdn.microsoft.com/library/windows/desktop/dd144904)  
  
- [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041)  
  
### <a name="example"></a>範例  
 下列程式碼範例示範如何呼叫`GetLogPen`擷取畫筆字元，並再建立新的實心筆使用相同的色彩。  
  
 [!code-cpp[NVC_MFCDocView #&103;](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]  
  
##  <a name="operator_hpen"></a>CPen::operator HPEN  
 取得附加的 Windows GDI 控制代碼的`CPen`物件。  
  
```  
operator HPEN() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼所代表`CPen`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，支援直接使用`HPEN`物件。  
  
 如需使用圖形物件的詳細資訊，請參閱文章[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&104;](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBrush 類別](../../mfc/reference/cbrush-class.md)

