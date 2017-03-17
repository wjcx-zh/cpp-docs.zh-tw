---
title: "CMFCEditBrowseCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- CMFCEditBrowseCtrl::PreTranslateMessage method
- CMFCEditBrowseCtrl constructor
- CMFCEditBrowseCtrl class
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
caps.latest.revision: 33
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5c5650da677a442628049c9ef4b41c2142cfb2c2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl 類別
`CMFCEditBrowseCtrl`類別支援編輯瀏覽控制項，這是選擇性包含瀏覽 按鈕可編輯文字方塊。 當使用者按一下瀏覽按鈕時，控制項就會執行自訂動作或顯示包含檔案瀏覽器或資料夾瀏覽器的標準對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCEditBrowseCtrl : public CEdit  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|預設建構函式。|  
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|啟用或停用 （隱藏） 瀏覽 按鈕。|  
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*檔案瀏覽*模式。|  
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|啟用 [瀏覽] 按鈕，然後將編輯瀏覽控制項放入*資料夾瀏覽*模式。|  
|[CMFCEditBrowseCtrl::GetMode](#getmode)|傳回目前的瀏覽模式。|  
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|編輯瀏覽控制項更新瀏覽動作的結果之後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|在使用者按一下 [瀏覽] 按鈕後，由架構呼叫。|  
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|目前的編輯瀏覽控制項來重新繪製。|  
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|若要繪製的瀏覽按鈕架構呼叫。|  
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|編輯控制項中輸入了不合法的檔案名稱時，由架構呼叫。|  
|`CMFCEditBrowseCtrl::PreTranslateMessage`|轉譯的視窗訊息，再分派給[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式。 如需語法和詳細資訊，請參閱[CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。|  
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|設定自訂的影像，以瀏覽 按鈕。|  
  
## <a name="remarks"></a>備註  
 使用 編輯瀏覽控制項來選取檔案或資料夾的名稱。 選擇性地使用控制項來執行自訂動作，例如顯示對話方塊。 您可以顯示或不會顯示 瀏覽 按鈕，並將自訂標籤或映像套用 按鈕。  
  
 *瀏覽模式*編輯瀏覽的控制項可以決定是否會顯示瀏覽 按鈕，並按一下按鈕時，就會發生什麼動作。 如需詳細資訊，請參閱[GetMode](#getmode)方法。  
  
 `CMFCEditBrowseCtrl`類別支援下列模式。  
  
 `custom mode`  
 使用者按一下 [瀏覽] 按鈕時執行自訂動作。 例如，您可以顯示應用程式特有的對話方塊。  
  
 `file mode`  
 當使用者按一下 [瀏覽] 按鈕，就會顯示標準檔案選取對話方塊。  
  
 `folder mode`  
 當使用者按一下 瀏覽 按鈕，就會顯示標準的資料夾選項 對話方塊。  
  
## <a name="how-to-specify-an-edit-browse-control"></a>How to︰ 指定編輯瀏覽控制項  
 執行下列步驟，以納入您的應用程式中編輯瀏覽控制項︰  
  
1.  如果您想要實作自訂的瀏覽模式時，衍生您自己從`CMFCEditBrowseCtrl`類別，然後覆寫[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)方法。 在覆寫方法中，執行自訂瀏覽動作並編輯瀏覽控制項以更新結果。  
  
2.  內嵌是`CMFCEditBrowseCtrl`物件，或者衍生的編輯瀏覽控制項的父視窗物件。  
  
3.  如果您使用**類別精靈**要建立對話方塊中，新增 編輯控制項 ( `CEdit`) 至對話方塊中的表單。 此外，加入變數，以存取標頭檔中的控制項。 在標頭檔中，變更 從變數的型別`CEdit`到`CMFCEditBrowseCtrl`。 編輯瀏覽控制項將會自動建立。 如果您不使用**類別精靈**，加入`CMFCEditBrowseCtrl`變數設為您的標頭檔，然後呼叫其`Create`方法。  
  
4.  如果您將編輯瀏覽控制項加入對話方塊中，使用**ClassWizard**工具來設定資料交換。  
  
5.  呼叫[EnableFolderBrowseButton](#enablefolderbrowsebutton)， [EnableFileBrowseButton](#enablefilebrowsebutton)，或[EnableBrowseButton](#enablebrowsebutton)方法來設定瀏覽模式和顯示瀏覽 按鈕。 呼叫[GetMode](#getmode)方法，以取得目前的瀏覽模式。  
  
6.  若要提供自訂映像瀏覽 按鈕，呼叫[SetBrowseButtonImage](#setbrowsebuttonimage)方法或覆寫[OnDrawBrowseButton](#ondrawbrowsebutton)方法。  
  
7.  若要移除編輯瀏覽控制項瀏覽 按鈕，請呼叫[EnableBrowseButton](#enablebrowsebutton)方法`bEnable`參數設定為`FALSE`。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)  
  
## <a name="example"></a>範例  
 下列範例示範如何使用在兩種方法`CMFCEditBrowseCtrl`類別︰`EnableFolderBrowseButton`和`EnableFileBrowseButton`。 這個範例是屬於[新的控制項範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&6;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls #&7;](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxeditbrowsectrl.h  
  
##  <a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton  
 顯示或不會顯示目前的編輯瀏覽控制項上的 [瀏覽] 按鈕。  
  
```  
void EnableBrowseButton(
    BOOL bEnable=TRUE,  
    LPCTSTR szLabel=_T("..."));
```  
  
### <a name="parameters"></a>參數  
 `bEnable`  
 `TRUE`若要顯示 [瀏覽] 按鈕。`FALSE`不想再顯示 [瀏覽] 按鈕。 預設值是 `TRUE`。  
  
 `szLabel`  
 瀏覽 按鈕顯示標籤。 預設值是" **...**".  
  
### <a name="remarks"></a>備註  
 如果`bEnable`參數是`TRUE`，實作自訂動作，按一下 [瀏覽] 按鈕時執行。 若要實作自訂動作，衍生自`CMFCEditBrowseCtrl`類別，然後覆寫其[OnBrowse](#onbrowse)方法。  
  
 如果`bEnable`參數是`TRUE`，控制項的瀏覽模式是`BrowseMode_Default`; 否則，請瀏覽模式`BrowseMode_None`。 如需瀏覽模式的詳細資訊，請參閱[GetMode](#getmode)方法。  
  
##  <a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton  
 在目前的編輯瀏覽控制項上顯示 [瀏覽] 按鈕，然後將控制項放入*檔案瀏覽*模式。  
  
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
 在目前的編輯瀏覽控制項上顯示 [瀏覽] 按鈕，然後將控制項放入*資料夾瀏覽*模式。  
  
```  
void EnableFolderBrowseButton();
```  
  
### <a name="remarks"></a>備註  
 當編輯瀏覽控制項是在資料夾瀏覽模式中，使用者按一下瀏覽 按鈕時，控制項會顯示標準的資料夾選項 對話方塊。  
  
##  <a name="getmode"></a>CMFCEditBrowseCtrl::GetMode  
 擷取目前的編輯瀏覽控制項的瀏覽模式。  
  
```  
CMFCEditBrowseCtrl::BrowseMode GetMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 其中一個列舉值，指定目前的編輯模式瀏覽控制項。 瀏覽模式會決定是否，架構會顯示 [瀏覽] 按鈕，在使用者按一下該按鈕時，就會發生什麼動作。  
  
 下表列出可能的傳回值。  
  
|值|描述|  
|-----------|-----------------|  
|`BrowseMode_Default`|`custom mode`. 程式設計人員定義的動作會執行。|  
|`BrowseMode_File`|`file mode`. 標準檔案瀏覽器 對話方塊隨即出現。|  
|`BrowseMode_Folder`|`folder mode`. 標準資料夾瀏覽器 對話方塊隨即出現。|  
|`BrowseMode_None`|不會顯示 [瀏覽] 按鈕。|  
  
### <a name="remarks"></a>備註  
 根據預設，`CMFCEditBrowseCtrl`物件會初始化為`BrowseMode_None`模式。 修改與瀏覽模式[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)， [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)，和[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)方法。  
  
##  <a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate  
 編輯瀏覽控制項更新瀏覽動作的結果之後，由架構呼叫。  
  
```  
virtual void OnAfterUpdate();
```  
  
### <a name="remarks"></a>備註  
 若要實作自訂動作的衍生類別中，這個方法會覆寫。  
  
##  <a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse  
 在使用者按一下編輯瀏覽控制項的 [瀏覽] 按鈕後，由架構呼叫。  
  
```  
virtual void OnBrowse();
```  
  
### <a name="remarks"></a>備註  
 使用這個方法來執行自訂程式碼，當使用者按一下編輯瀏覽控制項的 [瀏覽] 按鈕。 衍生您自己從`CMFCEditBrowseCtrl`類別並覆寫其`OnBrowse`方法。 在該方法，實作自訂瀏覽動作，並選擇性地更新編輯瀏覽控制項的文字方塊。 在您的應用程式使用[EnableBrowseButton](#enablebrowsebutton)方法，以編輯瀏覽控制項置於*自訂瀏覽*模式。  
  
##  <a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout  
 目前的編輯瀏覽控制項來重新繪製。  
  
```  
virtual void OnChangeLayout();
```  
  
### <a name="remarks"></a>備註  
 瀏覽模式的編輯瀏覽控制的變更時，架構會呼叫這個方法。 如需詳細資訊，請參閱[CMFCEditBrowseCtrl::GetMode](#getmode)。  
  
##  <a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton  
 在 編輯瀏覽控制項上繪製瀏覽按鈕架構呼叫。  
  
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
 瀏覽 按鈕，這個周框。  
  
 `bIsButtonPressed`  
 `TRUE`如果按下按鍵時。否則， `FALSE`。  
  
 `bIsButtonHot`  
 `TRUE`如果按鈕會反白顯示。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 覆寫這個函式在衍生的類別，即可自訂瀏覽 按鈕的外觀。  
  
##  <a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage  
 設定自訂映像編輯瀏覽控制項的 [瀏覽] 按鈕。  
  
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
 點陣圖的資源識別碼。  
  
 `bAutoDestroy`  
 `TRUE`刪除指定的圖示或點陣圖，當這個方法會結束。否則， `FALSE`。 預設值是 `TRUE`。  
  
### <a name="remarks"></a>備註  
 使用此方法的自訂映像用於瀏覽 按鈕。 根據預設，架構會取得標準映像中編輯瀏覽控制項時*檔案瀏覽*或*資料夾瀏覽*模式。  
  
##  <a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName  
 編輯控制項中輸入了不合法的檔案名稱時，由架構呼叫。  
  
```  
virtual BOOL OnIllegalFileName(CString& strFileName);
```  
  
### <a name="parameters"></a>參數  
 `strFileName`  
 指定不合法的檔案名稱。  
  
### <a name="return-value"></a>傳回值  
 應該會傳回`FALSE`如果此檔案名稱不能傳遞進一步 [檔案] 對話方塊。 在此情況下，焦點設回編輯控制項，使用者應該繼續編輯。 預設實作會顯示訊息方塊告知使用者有關的不合法的檔案名稱，並傳回`FALSE`。 您可以覆寫這個方法，更正檔案名稱，並傳回`TRUE`供進一步處理。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

