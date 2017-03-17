---
title: "CBitmapButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
dev_langs:
- C++
helpviewer_keywords:
- buttons, bitmap
- CBitmapButton class
- bitmaps, button controls
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
caps.latest.revision: 22
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
translationtype: Machine Translation
ms.sourcegitcommit: 0b07f6b12e178d8e324313ea3b0f6de9ae7420c9
ms.openlocfilehash: 16d39cb380b75e6dcef71dda01626f120d5c12fb
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmapbutton-class"></a>CBitmapButton 類別
建立以點陣圖影像 (而非文字) 標記的按鈕控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CBitmapButton : public CButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|建構 `CBitmapButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmapButton::AutoLoad](#autoload)|在對話方塊中的按鈕關聯的物件`CBitmapButton`類別名稱，以載入 bitmap(s) 和調整大小以符合點陣圖按鈕。|  
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|藉由從應用程式的資源檔載入一個或多個具名的點陣圖資源，並附加至物件的點陣圖中初始化的物件。|  
|[CBitmapButton::SizeToContent](#sizetocontent)|調整大小以容納點陣圖。|  
  
## <a name="remarks"></a>備註  
 `CBitmapButton`物件包含多達四個點陣圖，包含影像代表不同狀態的按鈕可以假設︰ 最新 （或標準），向下 （或選取），已取得焦點，且已停用。 第一次的點陣圖是必要的。有些則是選擇性的。  
  
 點陣圖按鈕映像包含影像，以及映像本身周圍的框線。 框線通常扮演顯示按鈕的狀態。 例如，焦點狀態的點陣圖通常是類似的最新狀態，但從框線或邊界粗實線虛線的矩形內凹。 點陣圖停用狀態通常是針對類似維持在最新狀態，但有較低的對比 （例如灰色或灰色功能表選項）。  
  
 這些點陣圖可以是任何規模大小，但所有被視為相同的大小維持在最新狀態的點陣圖。  
  
 各種應用程式會要求點陣圖影像的不同組合︰  
  
|上移|下移|已取得焦點|已停用|應用程式|  
|--------|----------|-------------|--------------|-----------------|  
|×||||Bitmap|  
|×|×|||按鈕沒有**WS_TABSTOP**樣式|  
|×|×|×|×|所有狀態對話方塊 按鈕|  
|×|×|×||使用對話方塊按鈕**WS_TABSTOP**樣式|  
  
 建立點陣圖按鈕控制項時，設定**BS_OWNERDRAW**以指定的按鈕是擁有者繪製樣式。 這會使 Windows 傳送`WM_MEASUREITEM`和`WM_DRAWITEM`訊息 按鈕，架構會處理這些訊息，並為您的按鈕外觀。  
  
### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在視窗的工作區中建立的點陣圖按鈕控制項  
  
1.  建立一到四個點陣圖影像的按鈕。  
  
2.  建構[CBitmapButton](#cbitmapbutton)物件。  
  
3.  呼叫[建立](../../mfc/reference/cbutton-class.md#create)函式來建立 Windows 按鈕控制項，並將其附加至`CBitmapButton`物件。  
  
4.  呼叫[LoadBitmaps](#loadbitmaps)成員函式來建構點陣圖按鈕後載入的點陣圖資源。  
  
### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>若要在對話方塊中包含點陣圖按鈕控制項  
  
1.  建立一到四個點陣圖影像的按鈕。  
  
2.  建立具有主控描繪按鈕位於您想要的點陣圖按鈕的對話方塊範本。 在範本中按鈕的大小並不重要。  
  
3.  將按鈕的標題設定值，例如 「 **MYIMAGE**」 和定義按鈕的符號，例如**IDC_MYIMAGE**。  
  
4.  在您的應用程式資源指令碼，讓每一個影像建立按鈕加上字母"U，""D，""F，"其中 ID 或者"X"（例如，清單中已取得焦點，且停用） 用於按鈕標題中的字串步驟 3。 按鈕標題 」 **MYIMAGE**，」 是識別碼，例如" **MYIMAGEU**，」 」 **MYIMAGED**，」 」 **MYIMAGEF**，"和" **MYIMAGEX**。 」 您**必須**指定雙引號括住您點陣圖的 ID。 否則資源編輯器會將整數指派給資源，並載入影像時，MFC 將會失敗。  
  
5.  您的應用程式的對話方塊類別 (衍生自`CDialog`)，加入`CBitmapButton`成員物件。  
  
6.  在`CDialog`物件的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)常式，呼叫`CBitmapButton`物件的[AutoLoad](#autoload)函數，做為參數使用按鈕的控制項 ID 和`CDialog`物件的**這**指標。  
  
 如果您想要處理 Windows 通知訊息，例如**BN_CLICKED**、 傳送至其父代的點陣圖按鈕控制項 (通常是一個類別衍生自**CDialog)**，加入`CDialog`-衍生物件訊息對應項目和訊息處理常式成員函式，為每個訊息。 傳送的告知`CBitmapButton`物件是由傳送那些相同[CButton](../../mfc/reference/cbutton-class.md)物件。  
  
 類別[CToolBar](../../mfc/reference/ctoolbar-class.md)點陣圖按鈕採取不同的方法。  
  
 如需有關`CBitmapButton`，請參閱[控制項](../../mfc/controls-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CBitmapButton`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxext.h  
  
##  <a name="autoload"></a>CBitmapButton::AutoLoad  
 在對話方塊中的按鈕關聯的物件`CBitmapButton`類別名稱，以載入 bitmap(s) 和調整大小以符合點陣圖按鈕。  
  
```  
BOOL AutoLoad(
    UINT nID,  
    CWnd* pParent);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 按鈕的控制項 id。  
  
 `pParent`  
 擁有按鈕物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`AutoLoad`函式來初始化對話方塊主控描繪按鈕點陣圖按鈕。 如 < 備註 > 中有使用這個函式指示`CBitmapButton`類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&75;](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]  
  
##  <a name="cbitmapbutton"></a>CBitmapButton::CBitmapButton  
 建立 `CBitmapButton` 物件。  
  
```  
CBitmapButton();
```  
  
### <a name="remarks"></a>備註  
 建立 c + + 之後`CBitmapButton`物件，請呼叫[CButton::Create](../../mfc/reference/cbutton-class.md#create)建立 Windows 按鈕控制項，並將其附加至`CBitmapButton`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&57;](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]  
  
##  <a name="loadbitmaps"></a>CBitmapButton::LoadBitmaps  
 使用此函式，當您想要載入其資源名稱或識別碼編號，或無法使用時的點陣圖影像`AutoLoad`函數，因為，比方說，您要建立不屬於 對話方塊中的點陣圖按鈕。  
  
```  
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,  
    LPCTSTR lpszBitmapResourceSel = NULL,  
    LPCTSTR lpszBitmapResourceFocus = NULL,  
    LPCTSTR lpszBitmapResourceDisabled = NULL);

 
BOOL LoadBitmaps(
    UINT nIDBitmapResource,  
    UINT nIDBitmapResourceSel = 0,  
    UINT nIDBitmapResourceFocus = 0,  
    UINT nIDBitmapResourceDisabled = 0);
```  
  
### <a name="parameters"></a>參數  
 *lpszBitmapResource*  
 指向以 null 結束的字串，其中包含適用於點陣圖按鈕的標準或 「 向上 」 狀態的點陣圖名稱。 必要項。  
  
 *lpszBitmapResourceSel*  
 指向以 null 終止的字串，其中包含選取點陣圖按鈕點陣圖的名稱或 「 向下 」 狀態。 可能是**NULL**。  
  
 *lpszBitmapResourceFocus*  
 指向以 null 結束的字串，其中包含點陣圖按鈕的焦點狀態點陣圖的名稱。 可能是**NULL**。  
  
 *lpszBitmapResourceDisabled*  
 指向以 null 結束的字串，其中包含點陣圖按鈕已停用狀態的點陣圖的名稱。 可能是**NULL**。  
  
 *nIDBitmapResource*  
 指定的點陣圖按鈕的標準或 「 向上 」 狀態的點陣圖資源的資源 ID 編號。 必要項。  
  
 *nIDBitmapResourceSel*  
 選取點陣圖按鈕或是 「 向下 」 狀態，請指定點陣圖資源的資源 ID 編號。 可能是 0。  
  
 *nIDBitmapResourceFocus*  
 指定的點陣圖按鈕具有焦點狀態的點陣圖資源的資源 ID 編號。 可能是 0。  
  
 *nIDBitmapResourceDisabled*  
 指定的點陣圖按鈕已停用狀態的點陣圖資源的資源 ID 編號。 可能是 0。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&58;](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]  
  
##  <a name="sizetocontent"></a>CBitmapButton::SizeToContent  
 呼叫此函式可調整大小的點陣圖大小的點陣圖按鈕。  
  
```  
void SizeToContent();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog #&59;](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CTRLTEST](../../visual-cpp-samples.md)   
 [CButton 類別](../../mfc/reference/cbutton-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


