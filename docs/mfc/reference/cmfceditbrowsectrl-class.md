---
title: "CMFCEditBrowseCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: de1e30e6ca9f404199c6db43837f35d612a02b69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|啟用或停用 （隱藏） 瀏覽 按鈕。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*檔案瀏覽*模式。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*瀏覽資料夾*模式。|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|傳回目前的瀏覽模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|在瀏覽動作的結果會更新編輯瀏覽控制項之後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在使用者按一下瀏覽按鈕之後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|重新繪製目前編輯瀏覽控制項。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|由架構呼叫以繪製瀏覽 按鈕。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|編輯控制項中輸入了不合法的檔案名稱時，由架構呼叫。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|將視窗訊息轉譯分派至之前[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需語法和詳細資訊，請參閱[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|設定瀏覽按鈕的自訂映像。|  
  
## <a name="remarks"></a>備註  
 使用編輯瀏覽控制項，來選取檔案或資料夾的名稱。 （選擇性） 使用的控制項來執行自訂動作，例如，若要顯示的對話方塊。 您可以顯示或不會顯示 瀏覽 按鈕，您可以套用自訂標籤或映像 5d; 按鈕。  
  
 *瀏覽模式*編輯瀏覽的控制項會決定是否會顯示 [瀏覽] 按鈕，並在按下按鈕時，就會發生什麼動作。 如需詳細資訊，請參閱[GetMode](#getmode)方法。  
  
 `CMFCEditBrowseCtrl`類別支援下列模式。  
  
 `custom mode`  
 當使用者按一下瀏覽按鈕時，會執行自訂動作。 例如，您可以顯示特定應用程式的對話方塊。  
  
 `file mode`  
 當使用者按一下瀏覽按鈕時，會顯示標準檔案選取對話方塊。  
  
 `folder mode`  
 當使用者按一下瀏覽按鈕時，會顯示標準資料夾選取對話方塊。  
  
## <a name="how-to-specify-an-edit-browse-control"></a>如何： 指定編輯瀏覽控制項  
 執行下列步驟以納入您的應用程式中編輯瀏覽控制項：  
  
1.  如果您想要實作自訂瀏覽模式時，衍生您自己從`CMFCEditBrowseCtrl`類別，然後覆寫[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)方法。 在覆寫方法中，執行自訂瀏覽動作，並以結果更新編輯瀏覽控制項。  
  
2.  將 內嵌`CMFCEditBrowseCtrl`物件或衍生的編輯瀏覽控制項物件的父視窗物件。  
  
3.  如果您使用**類別精靈**若要建立對話方塊中，將 編輯控制項 ( `CEdit`) 至對話方塊表單。 此外，加入變數，以存取標頭檔中的控制項。 在標頭檔中，變更 來自變數的型別`CEdit`至`CMFCEditBrowseCtrl`。 編輯瀏覽控制項將會自動建立。 如果您未使用**類別精靈**，新增`CMFCEditBrowseCtrl`變數設為您的標頭檔，然後再呼叫其`Create`方法。  
  
4.  如果您將編輯瀏覽控制項加入對話方塊中，使用**ClassWizard**工具來設定資料交換。  
  
5.  呼叫[EnableFolderBrowseButton](#enablefolderbrowsebutton)， [EnableFileBrowseButton](#enablefilebrowsebutton)，或[EnableBrowseButton](#enablebrowsebutton)方法以設定瀏覽模式，並顯示 [瀏覽] 按鈕。 呼叫[GetMode](#getmode)方法，以取得目前的瀏覽模式。  
  
6.  若要瀏覽按鈕提供的自訂映像，呼叫[SetBrowseButtonImage](#setbrowsebuttonimage)方法或覆寫[OnDrawBrowseButton](#ondrawbrowsebutton)方法。  
  
7.  若要移除編輯瀏覽控制項的瀏覽按鈕，請呼叫[EnableBrowseButton](#enablebrowsebutton)方法`bEnable`參數設定為`FALSE`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用兩種方法在`CMFCEditBrowseCtrl`類別：`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 這個範例是屬於[新控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 顯示或不會顯示目前編輯瀏覽控制項上的瀏覽按鈕。  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 `TRUE`若要顯示 [瀏覽] 按鈕。`FALSE`不想再顯示瀏覽按鈕。 預設值是 `TRUE`。  
  
 `szLabel`  
 瀏覽按鈕顯示標籤。 預設值是" **...**".  
  
### <a name="remarks"></a>備註  
 如果`bEnable`參數是`TRUE`，實作自訂動作，按一下瀏覽按鈕時執行。 若要實作自訂動作，衍生自`CMFCEditBrowseCtrl`類別，然後覆寫其[OnBrowse](#onbrowse)方法。  
  
 如果`bEnable`參數是`TRUE`，控制項的瀏覽模式是`BrowseMode_Default`; 否則，請瀏覽模式`BrowseMode_None`。 如需瀏覽模式的詳細資訊，請參閱[GetMode](#getmode)方法。  
  
##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 瀏覽按鈕會顯示目前編輯瀏覽控制項，並將控制項放在*檔案瀏覽*模式。  
  
```  
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,  
    LPCTSTR lpszFilter=NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```  
  
### <a name="parameters"></a>參數  
 `lpszDefExt`  
 指定用於檔案選取對話方塊中的預設副檔名。 預設值是 `NULL`。  
  
 `lpszFilter`  
 指定用於檔案選取對話方塊中的預設篩選字串。 預設值是 `NULL`。  
  
 `dwFlags`  
 對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽控制項處於檔案瀏覽模式時，若使用者按一下 [瀏覽] 按鈕，控制項將會顯示標準檔案選取對話方塊。  
  
 如需可用旗標的完整清單，請參閱[OPENFILENAME 結構](https://msdn.microsoft.com/library/ms646839.aspx)。  
  
##  <a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton  
 瀏覽按鈕會顯示目前編輯瀏覽控制項，並將控制項放在*瀏覽資料夾*模式。  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽控制項處於資料夾瀏覽模式，且使用者按一下瀏覽按鈕時，控制項就會顯示標準的資料夾的 [選取範圍] 對話方塊。  
  
##  <a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 擷取目前編輯瀏覽控制項的瀏覽模式。  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個列舉值，指定目前的編輯模式瀏覽控制項。 瀏覽模式會決定是否 framework 顯示在瀏覽按鈕，使用者按一下該按鈕時，就會發生什麼動作。  
  
 下表列出可能的傳回值。  
  
|值|描述|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`. 程式設計人員定義的動作會執行。|  
|`BrowseMode_File`|`file mode`. 會顯示標準檔案瀏覽器對話方塊。|  
|`BrowseMode_Folder`|`folder mode`. 標準資料夾瀏覽器 對話方塊隨即出現。|  
|`BrowseMode_None`|不會顯示瀏覽按鈕。|  
  
### <a name="remarks"></a>備註  
 根據預設，`CMFCEditBrowseCtrl`物件會初始化為`BrowseMode_None`模式。 修改與瀏覽模式[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)， [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)，和[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)方法。  
  
##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 在瀏覽動作的結果會更新編輯瀏覽控制項之後，由架構呼叫。  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>備註  
 覆寫這個方法來實作自訂動作的衍生類別中。  
  
##  <a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 在使用者按一下編輯瀏覽控制項的瀏覽按鈕之後，由架構呼叫。  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>備註  
 使用這個方法來執行自訂程式碼，當使用者按一下編輯瀏覽控制項的瀏覽按鈕。 衍生您自己從`CMFCEditBrowseCtrl`類別並覆寫其`OnBrowse`方法。 在該方法中，實作自訂瀏覽動作，並選擇性地更新編輯瀏覽控制項的文字方塊。 在您的應用程式使用[EnableBrowseButton](#enablebrowsebutton)方法，以編輯瀏覽控制項置於*自訂瀏覽*模式。  
  
##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 重新繪製目前編輯瀏覽控制項。  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽的瀏覽模式控制變更時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CMFCEditBrowseCtrl::GetMode](#getmode)。  
  
##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 由架構呼叫以繪製上編輯瀏覽控制項的瀏覽 按鈕。  
  
```  
virtual void OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsButtonPressed,  
    BOOL bIsButtonHot);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 裝置內容的指標。  
  
 `Rect`  
 瀏覽按鈕的週框。  
  
 `bIsButtonPressed`  
 `TRUE`如果按下按鈕。否則， `FALSE`。  
  
 `bIsButtonHot`  
 `TRUE`如果按鈕會反白顯示。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 若要自訂瀏覽按鈕的外觀的衍生類別中的這個函式會覆寫。  
  
##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
 編輯瀏覽控制項的瀏覽按鈕上設定的自訂映像。  
  
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
 `hIcon`  
 圖示的控制代碼。  
  
 `hBitmap`  
 點陣圖的控制代碼。  
  
 `uiBmpResId`  
 點陣圖的資源 ID。  
  
 `bAutoDestroy`  
 `TRUE`刪除指定的圖示或點陣圖，當這個方法會結束。否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 使用這個方法的自訂映像套用到瀏覽 按鈕。 根據預設，架構會取得標準映像時編輯瀏覽控制項處於*檔案瀏覽*或*瀏覽資料夾*模式。  
  
##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 編輯控制項中輸入了不合法的檔案名稱時，由架構呼叫。  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>參數  
 `strFileName`  
 指定不合法的檔案名稱。  
  
### <a name="return-value"></a>傳回值  
 應傳回`FALSE`如果此檔案名稱不能傳遞進一步 [檔案] 對話方塊。 在此情況下，焦點設回編輯控制項，使用者應該繼續編輯。 預設實作會顯示訊息方塊，告訴使用者關於不合法的檔案名稱，並傳回`FALSE`。 您可以覆寫這個方法，更正檔案的名稱，並傳回`TRUE`以便進一步處理。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)
