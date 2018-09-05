---
title: CMFCEditBrowseCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27a96082f620a09687102dd3fd42e6253968f2f7
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693968"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 類別
`CMFCEditBrowseCtrl`類別支援編輯瀏覽控制項，這是選擇性包含瀏覽 按鈕可編輯的文字方塊。 當使用者按一下瀏覽按鈕時，控制項就會執行自訂動作或顯示包含檔案瀏覽器或資料夾瀏覽器的標準對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|預設建構函式。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Enablebrowsebutton](#enablebrowsebutton)|啟用或停用 （隱藏） [瀏覽] 按鈕。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*檔案瀏覽*模式。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*瀏覽資料夾*模式。|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|傳回目前的瀏覽模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|編輯瀏覽控制項更新瀏覽動作的結果之後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在使用者按一下瀏覽按鈕之後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|會重新繪製目前編輯瀏覽控制項。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由架構呼叫以繪製瀏覽 按鈕。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|當編輯控制項中所輸入的不合法的檔案名稱時，由架構呼叫。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|將轉譯視窗訊息，再將它們分派至[TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)並[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) Windows 函式。 如需語法和詳細資訊，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|設定瀏覽按鈕的自訂映像。|  
  
## <a name="remarks"></a>備註  
 使用 編輯瀏覽控制項來選取檔案或資料夾的名稱。 （選擇性） 使用控制項來執行自訂動作，例如，若要顯示的對話方塊。 您可以顯示或不會顯示 [瀏覽] 按鈕，並可以在按鈕上套用的自訂標籤或映像。  
  
 *瀏覽模式*編輯瀏覽的控制會決定是否會顯示 [瀏覽] 按鈕，並按一下按鈕時，就會發生什麼動作。 如需詳細資訊，請參閱 < [GetMode](#getmode)方法。  
  
 `CMFCEditBrowseCtrl`類別支援下列模式。  
  
 **自訂模式**  
 當使用者按一下 [瀏覽] 按鈕時，會執行自訂動作。 例如，您可以顯示的應用程式特定的對話方塊。  
  
 **檔案模式**  
 當使用者按一下 [瀏覽] 按鈕時，會顯示標準檔案選取對話方塊。  
  
 **資料夾模式**  
 當使用者按一下 瀏覽 按鈕時，會顯示標準的資料夾選項 對話方塊。  
  
## <a name="how-to-specify-an-edit-browse-control"></a>如何： 指定編輯瀏覽控制項  
 執行下列步驟，以納入您的應用程式中編輯瀏覽控制項：  
  
1.  如果您想要實作自訂的瀏覽模式時，衍生您自己的類別，從`CMFCEditBrowseCtrl`類別，然後再覆寫[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)方法。 在覆寫方法中，執行自訂瀏覽動作，並以結果更新編輯瀏覽控制項。  
  
2.  內嵌是`CMFCEditBrowseCtrl`物件或衍生的編輯瀏覽控制項物件的父視窗物件。  
  
3.  如果您使用**類別精靈**若要建立對話方塊中，新增 編輯控制項 ( `CEdit`) 至對話方塊表單中。 此外，新增一個變數來存取您的標頭檔中的控制項。 在標頭檔案中，變更 來自變數的型別`CEdit`至`CMFCEditBrowseCtrl`。 編輯瀏覽控制項將會自動建立。 如果您不要使用**類別精靈**，新增`CMFCEditBrowseCtrl`變數設為您的標頭檔，然後呼叫其`Create`方法。  
  
4.  如果您將編輯瀏覽控制項加入對話方塊中，使用**ClassWizard**工具來設定資料交換。  
  
5.  呼叫[EnableFolderBrowseButton](#enablefolderbrowsebutton)， [EnableFileBrowseButton](#enablefilebrowsebutton)，或[EnableBrowseButton](#enablebrowsebutton)方法來設定瀏覽模式，並顯示 [瀏覽] 按鈕。 呼叫[GetMode](#getmode)方法，以取得目前的瀏覽模式。  
  
6.  若要瀏覽按鈕提供自訂映像，請呼叫[SetBrowseButtonImage](#setbrowsebuttonimage)方法或覆寫[OnDrawBrowseButton](#ondrawbrowsebutton)方法。  
  
7.  若要移除編輯瀏覽控制項中的 [瀏覽] 按鈕，請呼叫[EnableBrowseButton](#enablebrowsebutton)方法*bEnable*參數設定為 FALSE。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用兩種方法中的`CMFCEditBrowseCtrl`類別：`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>  Enablebrowsebutton  
 顯示或不會顯示目前編輯瀏覽控制項上的 [瀏覽] 按鈕。  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>參數  
 *bEnable*  
 若要顯示 [瀏覽] 按鈕;，則為 TRUE不想再顯示 [瀏覽] 按鈕，則為 FALSE。 預設值為 TRUE。  
  
 *szLabel*  
 瀏覽 按鈕顯示標籤。 預設值是" **...**".  
  
### <a name="remarks"></a>備註  
 如果*bEnable*參數為 TRUE，實作自訂動作，以在按一下 [瀏覽] 按鈕時執行。 若要實作自訂動作，衍生的類別`CMFCEditBrowseCtrl`類別，然後再覆寫其[OnBrowse](#onbrowse)方法。  
  
 如果*bEnable*參數為 TRUE，控制項的瀏覽模式`BrowseMode_Default`; 否則，請瀏覽模式`BrowseMode_None`。 如需有關瀏覽模式的詳細資訊，請參閱[GetMode](#getmode)方法。  
  
##  <a name="enablefilebrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFileBrowseButton  
 瀏覽按鈕會顯示目前編輯瀏覽控制項，並將控制項放在*檔案瀏覽*模式。  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>參數  
 *lpszDefExt*  
 指定用於檔案選取對話方塊中的預設副檔名。 預設值是 NULL。  
  
 *lpszFilter*  
 指定用於檔案選取對話方塊中的預設篩選字串。 預設值是 NULL。  
  
 *dwFlags*  
 對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽控制項處於檔案瀏覽模式時，若使用者按一下 [瀏覽] 按鈕，控制項將會顯示標準檔案選取對話方塊。  
  
 可用的旗標完整清單，請參閱 < [OPENFILENAME 結構](/windows/desktop/api/commdlg/ns-commdlg-tagofna)。  
  
##  <a name="enablefolderbrowsebutton"></a>  CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 瀏覽按鈕會顯示目前編輯瀏覽控制項，並將控制項放在*瀏覽資料夾*模式。  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽控制項處於資料夾瀏覽模式且使用者按一下 [瀏覽] 按鈕時，控制項就會顯示標準的資料夾的 [選取項目] 對話方塊。  
  
##  <a name="getmode"></a>  CMFCEditBrowseCtrl::GetMode  
 擷取目前編輯瀏覽控制項的瀏覽模式。  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個列舉值，指定目前的編輯模式瀏覽控制項。 瀏覽模式會決定是否，架構會顯示 [瀏覽] 按鈕，和使用者按下該按鈕時，就會發生什麼動作。  
  
 下表列出可能的傳回值。  
  
|值|描述|  
|-----------|-----------------|  
|`BrowseMode_Default`|**自訂模式**。 程式設計人員定義的動作會執行。|  
|`BrowseMode_File`|**檔案模式**。 會顯示標準檔案瀏覽器對話方塊。|  
|`BrowseMode_Folder`|**資料夾模式**。 標準資料夾瀏覽器 對話方塊隨即出現。|  
|`BrowseMode_None`|不會顯示 [瀏覽] 按鈕。|  
  
### <a name="remarks"></a>備註  
 根據預設，`CMFCEditBrowseCtrl`物件會初始化為`BrowseMode_None`模式。 修改與瀏覽模式[Enablebrowsebutton](#enablebrowsebutton)， [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)，和[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)方法。  
  
##  <a name="onafterupdate"></a>  CMFCEditBrowseCtrl::OnAfterUpdate  
 編輯瀏覽控制項更新瀏覽動作的結果之後，由架構呼叫。  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>備註  
 覆寫此方法來實作自訂動作的衍生類別中。  
  
##  <a name="onbrowse"></a>  CMFCEditBrowseCtrl::OnBrowse  
 在使用者按一下 編輯瀏覽控制項的瀏覽按鈕之後，由架構呼叫。  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>備註  
 使用此方法來執行自訂程式碼，當使用者按一下 編輯瀏覽控制項的 瀏覽 按鈕。 衍生您自己的類別，從`CMFCEditBrowseCtrl`類別並覆寫其`OnBrowse`方法。 在該方法中，實作自訂的瀏覽動作，並選擇性地更新 編輯瀏覽控制項的文字方塊。 在您的應用程式中，使用[EnableBrowseButton](#enablebrowsebutton)方法，以編輯瀏覽控制項置於*自訂瀏覽*模式。  
  
##  <a name="onchangelayout"></a>  CMFCEditBrowseCtrl::OnChangeLayout  
 會重新繪製目前編輯瀏覽控制項。  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>備註  
 瀏覽模式的編輯瀏覽控制項變更時，架構會呼叫這個方法。 如需詳細資訊，請參閱 < [CMFCEditBrowseCtrl::GetMode](#getmode)。  
  
##  <a name="ondrawbrowsebutton"></a>  CMFCEditBrowseCtrl::OnDrawBrowseButton  
 由架構呼叫以繪製編輯瀏覽控制項上的 [瀏覽] 按鈕。  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>參數  
 *pDC*  
 裝置內容的指標。  
  
 *rect*  
 瀏覽按鈕的週框。  
  
 *bIsButtonPressed*  
 如果按下按鈕時，則為 TRUE否則為 FALSE。  
  
 *bIsButtonHot*  
 如果按鈕已反白顯示;，則為 TRUE。否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 若要自訂的瀏覽 按鈕外觀的衍生類別中此函式會覆寫。  
  
##  <a name="setbrowsebuttonimage"></a>  CMFCEditBrowseCtrl::SetBrowseButtonImage  
 在 編輯瀏覽控制項的 瀏覽 按鈕上設定自訂映像。  
  
```  
void SetBrowseButtonImage(
    HICON hIcon,  
    BOOL bAutoDestroy= TRUE);

 
void SetBrowseButtonImage(
    HBITMAP hBitmap,  
    BOOL bAutoDestroy= TRUE);  
  
void SetBrowseButtonImage(UINT uiBmpResId);
```  
  
### <a name="parameters"></a>參數  
 *hIcon*  
 圖示的控制代碼。  
  
 *hBitmap*  
 點陣圖的控制代碼。  
  
 *uiBmpResId*  
 點陣圖的資源 ID。  
  
 *bAutoDestroy*  
 當這個方法存在時，刪除指定的圖示或點陣圖，則為 TRUE否則為 FALSE。 預設值為 TRUE。  
  
### <a name="remarks"></a>備註  
 若要自訂的映像套用至瀏覽按鈕中使用這個方法。 根據預設，架構會取得標準映像時編輯瀏覽控制項處於*檔案瀏覽*或是*瀏覽資料夾*模式。  
  
##  <a name="onillegalfilename"></a>  CMFCEditBrowseCtrl::OnIllegalFileName  
 當編輯控制項中所輸入的不合法的檔案名稱時，由架構呼叫。  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>參數  
 *strFileName*  
 指定不合法的檔案名稱。  
  
### <a name="return-value"></a>傳回值  
 如果此檔案名稱不能傳遞進一步 [檔案] 對話方塊，則應傳回 FALSE。 在此案例中，焦點便會設定為編輯控制項，且使用者應該繼續編輯。 預設實作會顯示訊息方塊，告知使用者有關的不合法的檔案名稱，且會傳回 FALSE。 您可以覆寫這個方法、 更正檔案名稱，並傳回 TRUE，以便進一步處理。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
