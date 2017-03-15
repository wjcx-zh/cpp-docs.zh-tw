---
title: "CFileDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileDialog
dev_langs:
- C++
helpviewer_keywords:
- CFileDialog class
- common file dialog boxes
- dialog boxes, common
ms.assetid: fda4fd3c-08b8-4ce0-8e9d-7bab23f8c6c0
caps.latest.revision: 47
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
ms.openlocfilehash: 7cde10ee445a719bce6be4167698bd86c46a18c0
ms.lasthandoff: 02/24/2017

---
# <a name="cfiledialog-class"></a>CFileDialog 類別
封裝檔案開啟或儲存作業的檔案所用的通用對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class CFileDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileDialog::CFileDialog](#cfiledialog)|建構 `CFileDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileDialog::AddCheckButton](#addcheckbutton)|將對話方塊中的核取按鈕。|  
|[CFileDialog::AddComboBox](#addcombobox)|將下拉式方塊加入至對話方塊。|  
|[CFileDialog::AddControlItem](#addcontrolitem)|在對話方塊中的容器控制項中加入項目。|  
|[CFileDialog::AddEditBox](#addeditbox)|將編輯方塊加入至對話方塊。|  
|[CFileDialog::AddMenu](#addmenu)|將功能表加入至對話方塊。|  
|[CFileDialog::AddPlace](#addplace)|多載。 加入至清單的資料夾將適用於使用者開啟或儲存的項目。|  
|[CFileDialog::AddPushButton](#addpushbutton)|將按鈕加入至對話方塊。|  
|[CFileDialog::AddRadioButtonList](#addradiobuttonlist)|將選項按鈕 （也稱為選項按鈕） 群組加入至對話方塊。|  
|[CFileDialog::AddSeparator](#addseparator)|將對話方塊中的分隔符號。|  
|[CFileDialog::AddText](#addtext)|將文字內容加入至對話方塊。|  
|[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)|更新的狀態，`CFileDialog`比對參數和儲存在旗標`m_ofn`成員變數。|  
|[CFileDialog::DoModal](#domodal)|顯示對話方塊，並可讓使用者進行選擇。|  
|[CFileDialog::EnableOpenDropDown](#enableopendropdown)|下拉式清單，啟用**開啟**或**儲存**對話方塊中的按鈕。|  
|[CFileDialog::EndVisualGroup](#endvisualgroup)|加入的項目 對話方塊中的視覺化群組就會停止。|  
|[CFileDialog::GetCheckButtonState](#getcheckbuttonstate)|取得對話方塊中的核取按鈕 （核取方塊） 的目前狀態。|  
|[CFileDialog::GetControlItemState](#getcontrolitemstate)|取得目前的狀態 對話方塊中找到的容器控制項中的項目。|  
|[CFileDialog::GetControlState](#getcontrolstate)|取得目前的可見性，並啟用指定的控制項的狀態。|  
|[CFileDialog::GetEditBoxText](#geteditboxtext)|取得目前的文字編輯方塊控制項中。|  
|[CFileDialog::GetFileExt](#getfileext)|傳回所選檔案的副檔名。|  
|[CFileDialog::GetFileName](#getfilename)|傳回所選檔案的檔案名稱。|  
|[CFileDialog::GetFileTitle](#getfiletitle)|傳回所選檔案的標題。|  
|[CFileDialog::GetFolderPath](#getfolderpath)|擷取目前開啟的資料夾或目錄路徑的檔案總管樣式**開啟**或**另存新檔**通用對話方塊。|  
|[CFileDialog::GetIFileDialogCustomize](#getifiledialogcustomize)|擷取內部的 COM 物件的自訂`CFileDialog`物件。|  
|[CFileDialog::GetIFileOpenDialog](#getifileopendialog)|會擷取內部的 COM 物件`CFileDialog`作為**開啟**檔案 對話方塊。|  
|[CFileDialog::GetIFileSaveDialog](#getifilesavedialog)|會擷取內部的 COM 物件`CFileDialog`作為**儲存**檔案 對話方塊。|  
|[CFileDialog::GetNextPathName](#getnextpathname)|傳回下一步所選檔案的完整路徑。|  
|[CFileDialog::GetOFN](#getofn)|擷取`OPENFILENAME`結構`CFileDialog`物件。|  
|[CFileDialog::GetPathName](#getpathname)|傳回所選檔案的完整路徑。|  
|[CFileDialog::GetReadOnlyPref](#getreadonlypref)|傳回所選檔案的唯讀狀態。|  
|[CFileDialog::GetResult](#getresult)|取得對話方塊中的使用者所做的選擇。|  
|[CFileDialog::GetResults](#getresults)|在對話方塊中，可讓多個選取項目中取得使用者的選擇。|  
|[CFileDialog::GetSelectedControlItem](#getselectedcontrolitem)|從指定的容器控制項在對話方塊中，取得特定的項目。|  
|[CFileDialog::GetStartPosition](#getstartposition)|傳回的檔案名稱清單的第一個元素的位置。|  
|[CFileDialog::HideControl](#hidecontrol)|隱藏指定的控制項，在檔案總管樣式**開啟**或**另存新檔**通用對話方塊。|  
|[CFileDialog::IsPickFoldersMode](#ispickfoldersmode)|判斷目前對話方塊資料夾選擇器模式。|  
|[CFileDialog::MakeProminent](#makeprominent)|上的芳鄰 對話方塊中的控制項，讓它突出相較於其他新增的控制項。|  
|[CFileDialog::RemoveControlItem](#removecontrolitem)|在對話方塊中的容器控制項中移除的項目。|  
|[CFileDialog::SetCheckButtonState](#setcheckbuttonstate)|在對話方塊中設定的核取按鈕 （核取方塊） 的目前狀態。|  
|[CFileDialog::SetControlItemState](#setcontrolitemstate)|在對話方塊中找到的容器控制項中設定項目的目前狀態。|  
|[CFileDialog::SetControlItemText](#setcontrolitemtext)|設定控制項項目的文字。 例如，文字所附的選項按鈕或功能表項目。|  
|[CFileDialog::SetControlLabel](#setcontrollabel)|設定按鈕文字或編輯標籤等控制項，與相關聯的文字。|  
|[CFileDialog::SetControlState](#setcontrolstate)|設定目前的可見性，並啟用指定的控制項的狀態。|  
|[CFileDialog::SetControlText](#setcontroltext)|設定指定之控制項的文字，在檔案總管樣式**開啟**或**另存新檔**通用對話方塊。|  
|[CFileDialog::SetDefExt](#setdefext)|設定預設的副檔名的檔案總管樣式**開啟**或**另存新檔**通用對話方塊。|  
|[CFileDialog::SetEditBoxText](#seteditboxtext)|設定目前的文字編輯方塊控制項中。|  
|[CFileDialog::SetProperties](#setproperties)|提供屬性儲存區，可定義要用於所儲存之項目的預設值。|  
|[CFileDialog::SetSelectedControlItem](#setselectedcontrolitem)|選項按鈕群組或在對話方塊中找到下拉式方塊中設定特定項目的選取的狀態。|  
|[CFileDialog::SetTemplate](#settemplate)|設定的對話方塊範本`CFileDialog`物件。|  
|[CFileDialog::StartVisualGroup](#startvisualgroup)|宣告可見的群組，在對話方塊中。 任何 「 加入 」 方法的後續呼叫會將這些項目新增至此群組。|  
|[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)|更新資料儲存在`m_ofn`成員變數，以符合檔案對話方塊中的目前狀態。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFileDialog::OnButtonClicked](#onbuttonclicked)|按一下按鈕時呼叫。|  
|[CFileDialog::OnCheckButtonToggled](#oncheckbuttontoggled)|核取方塊已核取/取消核取時呼叫。|  
|[CFileDialog::OnControlActivating](#oncontrolactivating)|當控制項正在使用中時呼叫。|  
|[CFileDialog::OnFileNameChange](#onfilenamechange)|處理`WM_NOTIFY CDN_SELCHANGE`訊息。|  
|[CFileDialog::OnFileNameOK](#onfilenameok)|驗證對話方塊中輸入檔案名稱。|  
|[CFileDialog::OnFolderChange](#onfolderchange)|處理`WM_NOTIFY CDN_FOLDERCHANGE`訊息。|  
|[CFileDialog::OnInitDone](#oninitdone)|處理`WM_NOTIFY CDN_INITDONE`訊息。|  
|[CFileDialog::OnItemSelected](#onitemselected)|在選取的容器項目時呼叫。|  
|[CFileDialog::OnLBSelChangedNotify](#onlbselchangednotify)|可讓您的檔案選取範圍變更時執行自訂動作。|  
|[CFileDialog::OnShareViolation](#onshareviolation)|處理共用違規。|  
|[CFileDialog::OnTypeChange](#ontypechange)|處理`WM_NOTIFY CDN_TYPECHANGE`訊息。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CFileDialog::m_ofn](#m_ofn)|Windows`OPENFILENAME`結構。 提供基本檔案對話方塊方塊參數的存取權。|  
  
## <a name="remarks"></a>備註  
 通用檔案對話方塊能讓您實作檔案選取對話方塊中，例如**開啟檔案**和**另存新檔**，與 Windows 標準一致的方式。  
  
 您可以使用`CFileDialog`現狀提供，建構函式，或您可以衍生您自己的對話方塊類別從`CFileDialog`和寫入以符合您需求的建構函式。 在任一情況下，這些對話方塊的行為就像標準 MFC 對話方塊因為衍生自[CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)。 `CFileDialog`依賴 COMMDLG。包含在 Windows 中的 DLL 檔案。  
  
 外觀和功能的`CFileDialog`與[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]與舊版 Windows 的不同。 預設`CFileDialog`會自動使用新[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式，而如果編譯程式的程式碼變更下的執行[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 使用`bVistaStyle`手動覆寫這個自動更新建構函式中的參數。 自動更新的例外狀況是自訂的對話方塊。 它們不會轉換成新的樣式。 如需建構函式的詳細資訊，請參閱[CFileDialog::CFileDialog](#cfiledialog)。  
  
> [!NOTE]
>  在不同的控制項 ID 系統[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]從舊版的 Windows，當您使用`CFileDialog`。 您必須更新所有參考`CFileDialog`程式碼之前，您可以移植您的專案，從較早版本的 Windows 中的控制項。  
  
 某些`CFileDialog`方法不受[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 請檢查是否支援此方法的相關資訊的個別方法主題。 此外，下列繼承的函式不支援在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)  
  
- [CDialog::OnSetFont](../../mfc/reference/cdialog-class.md#onsetfont)  
  
 Windows 訊息`CFileDialog`類別根據您使用的作業系統而有所不同。 例如，不支援 Windows XP [CDialog::OnCancel](../../mfc/reference/cdialog-class.md#oncancel)和[CDialog::OnOK](../../mfc/reference/cdialog-class.md#onok)的`CFileDialog`類別。 不過，[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]支援它們。 如需不同所產生的訊息和接收它們的順序的詳細資訊，請參閱[CFileDialog 範例︰ 記錄的事件順序](../../visual-cpp-samples.md)。  
  
 若要使用`CFileDialog`物件，使用第一次建立物件`CFileDialog`建構函式。 在建構對話方塊之後，您可以設定或修改中的任何值[CFileDialog::m_ofn](#m_ofn)結構初始化的值或對話方塊控制項的狀態。 `m_ofn`結構的型別是`OPENFILENAME`。 如需詳細資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 初始化對話方塊的控制項之後，請呼叫[CFileDialog::DoModal](#domodal)方法來顯示對話方塊方塊，讓使用者可以輸入路徑和檔案名稱。 `DoModal`傳回使用者點選 [確定] (IDOK) 或 [取消 (IDCANCEL)] 按鈕。 如果`DoModal`傳回 IDOK，您可以使用其中一個`CFileDialog`public 成員函式來擷取資訊放入使用者。  
  
> [!NOTE]
>  在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，多個呼叫[IFileDialog::SetFileTypes](http://msdn.microsoft.com/library/windows/desktop/bb775980)會導致錯誤。 第二次呼叫`SetFileTypes`之執行個體`CFileDialog`會傳回`E_UNEXPECTED`中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 某些`CFileDialog`方法函式呼叫`SetFileTypes`。 例如，兩個呼叫`CFileDialog::DoModal`相同執行個體`CFileDialog`產生[ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c)。  
  
 `CFileDialog`包括幾個受保護的成員，讓您執行自訂處理共用違規，檔案名稱驗證，清單方塊變更通知。 這些受保護的成員是大部分的應用程式不需要使用，因為預設的處理會自動執行的回呼函式。 因為它們是標準的虛擬函式，並不需要這些函式的訊息對應項目。  
  
 您可以使用 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式判斷是否在對話方塊的初始化期間發生錯誤，並了解錯誤的詳細資訊。  
  
 損毀的`CFileDialog`物件會自動處理。 您不需要呼叫[CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog)。  
  
 若要讓使用者選取多個檔案，將`OFN_ALLOWMULTISELECT`旗標，才能呼叫`DoModal`。 您必須提供您自己來容納多個檔案名稱傳回的清單的檔案名稱緩衝區。 執行這項操作來取代`m_ofn.lpstrFile`與緩衝區的指標所配置的之後您建構, `CFileDialog`，但在呼叫之前`DoModal`。  
  
 此外，您必須設定`m_ofn.nMaxFile`所指向的緩衝區中使用的字元數`m_ofn.lpstrFile`。 如果您設定要選取的檔案數目上限`n`，所需的緩衝區大小是`n * (_MAX_PATH + 1) + 1`。 傳回緩衝區中的第一個項目是已在所選取檔案的資料夾路徑。 如[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]-樣式對話方塊、 目錄和檔案名稱的字串是 null 結尾，以額外的 null 字元之後的最後一個檔案名稱。 此格式可讓 [檔案總管樣式] 對話方塊，以傳回包含空格的長檔名。 舊式的對話方塊，以空格分隔的目錄和檔案名稱的字串和函式使用短檔名的檔案名稱包含空格。  
  
 下列範例示範如何使用緩衝區，來擷取，並列出多個檔案名稱。  
  
 [!code-cpp[NVC_MFCFiles #&23;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要變更以回應使用者選取多個檔案名稱的緩衝區大小，您必須衍生新的類別，從`CFileDialog`並覆寫[CFileDialog::OnFileNameChange](#onfilenamechange)方法。  
  
 如果您衍生新類別從`CFileDialog`，您可以使用訊息對應來處理任何訊息。 若要擴充的預設訊息處理，衍生自`CFileDialog`、 將訊息對應新增至新的類別，並提供成員函式的新訊息。 您沒有提供自訂對話方塊中的攔截函式。  
  
 若要自訂對話方塊中，衍生自`CFileDialog`、 提供自訂的對話方塊範本，以及加入訊息對應來處理從擴充的控制項通知訊息。 將任何未處理的訊息傳遞至基底類別。 您沒有自訂攔截函式。  
  
 當您使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式`CFileDialog`，您無法使用訊息對應和對話方塊範本。 相反地，您必須使用 COM 介面的類似功能。  
  
 如需有關如何使用`CFileDialog`，請參閱[通用對話方塊類別](../../mfc/common-dialog-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CFileDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdlgs.h  
  
##  <a name="a-nameaddcheckbuttona--cfiledialogaddcheckbutton"></a><a name="addcheckbutton"></a>CFileDialog::AddCheckButton  
 將對話方塊中的核取按鈕。  
  
```  
HRESULT AddCheckButton(
    DWORD dwIDCtl,  
    const CString& strLabel,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 加入核取按鈕識別碼。  
  
 `strLabel`  
 核取按鈕名稱。  
  
 `bChecked`  
 布林值，表示目前狀態的核取按鈕。 `TRUE`若選取此選項。`FALSE`否則  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddcomboboxa--cfiledialogaddcombobox"></a><a name="addcombobox"></a>CFileDialog::AddComboBox  
 將下拉式方塊加入至對話方塊。  
  
```  
HRESULT AddComboBox(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 要加入下拉式方塊的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddcontrolitema--cfiledialogaddcontrolitem"></a><a name="addcontrolitem"></a>CFileDialog::AddControlItem  
 在對話方塊中的容器控制項中加入項目。  
  
```  
HRESULT AddControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 將項目加入容器控制項的 ID。  
  
 `dwIDItem`  
 項目的識別碼。  
  
 `strLabel`  
 項目的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddeditboxa--cfiledialogaddeditbox"></a><a name="addeditbox"></a>CFileDialog::AddEditBox  
 將編輯方塊加入至對話方塊。  
  
```  
HRESULT AddEditBox(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 要新增的編輯方塊的識別碼。  
  
 `strText`  
 編輯方塊名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddmenua--cfiledialogaddmenu"></a><a name="addmenu"></a>CFileDialog::AddMenu  
 將功能表加入至對話方塊。  
  
```  
HRESULT AddMenu(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 要加入功能表的識別碼。  
  
 `strLabel`  
 功能表名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddplacea--cfiledialogaddplace"></a><a name="addplace"></a>CFileDialog::AddPlace  
 加入至清單的資料夾將適用於使用者開啟或儲存的項目。  
  
```  
void AddPlace(
    LPCWSTR lpszFolder,  
    FDAP fdap = FDAP_TOP) throw();

 
void AddPlace(
    IShellItem* psi,  
    FDAP fdap = FDAP_TOP) throw();
```  
  
### <a name="parameters"></a>參數  
 `lpszFolder`  
 可供使用者資料夾的路徑。 這只能是一個資料夾。  
  
 `fdap`  
 指定的資料夾清單中的放置位置。  
  
 `psi`  
 代表可供使用者資料夾 IShellItem 指標。 這只能是一個資料夾。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddpushbuttona--cfiledialogaddpushbutton"></a><a name="addpushbutton"></a>CFileDialog::AddPushButton  
 將按鈕加入至對話方塊。  
  
```  
HRESULT AddPushButton(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 若要新增按鈕的 ID。  
  
 `strLabel`  
 按鈕名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddradiobuttonlista--cfiledialogaddradiobuttonlist"></a><a name="addradiobuttonlist"></a>CFileDialog::AddRadioButtonList  
 將選項按鈕 （也稱為選項按鈕） 群組加入至對話方塊。  
  
```  
HRESULT AddRadioButtonList(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 要加入選項按鈕群組的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddseparatora--cfiledialogaddseparator"></a><a name="addseparator"></a>CFileDialog::AddSeparator  
 將對話方塊中的分隔符號。  
  
```  
HRESULT AddSeparator(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 加入分隔符號的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddtexta--cfiledialogaddtext"></a><a name="addtext"></a>CFileDialog::AddText  
 將文字加入至對話方塊。  
  
```  
HRESULT AddText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 若要新增的文字識別碼。  
  
 `strText`  
 文字的名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameapplyofntoshelldialoga--cfiledialogapplyofntoshelldialog"></a><a name="applyofntoshelldialog"></a>CFileDialog::ApplyOFNToShellDialog  
 更新的目前狀態[CFileDialog](../../mfc/reference/cfiledialog-class.md)值儲存在`m_ofn`資料結構。  
  
```  
void ApplyOFNToShellDialog();
```  
  
### <a name="remarks"></a>備註  
 在之前的 Windows 版本[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，成員[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)連續資料結構進行同步處理的狀態`CFileDialog`。 任何對[m_ofn](#m_ofn)成員變數立即反映在對話方塊中的狀態。 此外，任何對話方塊中的狀態變更立即更新`m_ofn`成員變數。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]中的值`m_ofn`成員變數和狀態`CFileDialog`不保證同步處理。 此函式會強制的狀態`CFileDialog`更新，以符合`m_ofn`結構。 Windows 會呼叫此函式期間自動[CFileDialog::DoModal](#domodal)。  
  
 如需有關如何使用`CFileDialog`類別下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)。  
  
##  <a name="a-namecfiledialoga--cfiledialogcfiledialog"></a><a name="cfiledialog"></a>CFileDialog::CFileDialog  
 呼叫此函式來建構標準 Windows 檔案對話方塊。  
  
```  
explicit CFileDialog(
    BOOL bOpenFileDialog,  
    LPCTSTR lpszDefExt = NULL,  
    LPCTSTR lpszFileName = NULL,  
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter = NULL,  
    CWnd* pParentWnd = NULL,  
    DWORD dwSize = 0,  
    BOOL bVistaStyle = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bOpenFileDialog`  
 指定的對話方塊來建立類型的參數。 將它設定為`TRUE`建構**開啟舊檔**對話方塊。 將它設定為`FALSE`建構**檔案另存新檔**對話方塊。  
  
 [in] `lpszDefExt`  
 預設的副檔名。 如果使用者不是已知的副檔名 （一個在使用者電腦上有關聯） 包含檔案名稱 方塊中，由指定副檔名`lpszDefExt`會自動附加至檔案名稱。 如果這個參數是`NULL`，沒有副檔名會附加。  
  
 [in] `lpszFileName`  
 初始檔案名稱出現在 [檔案名稱] 方塊中。 如果`NULL`，初始檔案名稱不會出現。  
  
 [in] `dwFlags`  
 您可以使用自訂對話方塊中的一或多個旗標的組合。 如需這些旗標的說明，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如果您修改`m_ofn.Flags`結構成員，請在您的變更中使用位元 OR 運算子，讓預設行為保持不變。  
  
 [in] `lpszFilter`  
 一系列的指定篩選條件的字串組可以套用至檔案。 如果您指定檔案篩選器時，符合篩選準則的檔案會出現在檔案清單。 請參閱 < 備註 > 一節，如需有關如何使用檔案篩選器。  
  
 [in] `pParentWnd`  
 檔案 對話方塊中的父系或擁有者視窗的指標。  
  
 [in] `dwSize`  
 大小`OPENFILENAME`結構。 這個值取決於作業系統版本。 MFC 使用這個參數來決定對話方塊來建立適當類型 (例如，new[!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)]對話方塊而不是 NT4 對話方塊)。 預設大小為 0 表示 MFC 程式碼會判斷要使用的正確對話方塊方塊大小會根據在程式執行的作業系統版本。  
  
 [in] `bVistaStyle`  
 **請注意**這個參數是可在 Visual Studio 2008 及更新版本，且會導致您在執行時，才可使用新樣式對話方塊[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]或更新版本。  
  
 參數會指定 [檔案] 對話方塊中的樣式。 將它設定為`TRUE`使用新的 Vista 樣式檔案對話方塊。 否則，您將使用舊樣式的對話方塊。 請參閱 < 備註 > 一節如需詳細資訊 Vista 下執行。  
  
### <a name="remarks"></a>備註  
 任一**開啟舊檔**或**檔案另存新檔**建構對話方塊時，根據的值`bOpenFileDialog`。  
  
 指定預設的延伸模組使用`lpszDefExt`可能不會產生行為預期不同，因為它不是可預測哪些延伸模組有使用者的電腦上的檔案關聯。 如果您需要更充分掌控附加的預設延伸模組，您可以衍生自己的類別，從`CFileDialog`，並覆寫`CFileDialog::OnFileNameOK`方法，以執行您自己的延伸模組處理。  
  
 若要讓使用者選取多個檔案，將`OFN_ALLOWMULTISELECT`旗標，才能呼叫[DoModal](#domodal)。 您必須提供儲存傳回多個檔案名稱的清單，您的檔案名稱緩衝區。 執行這項操作來取代`m_ofn.lpstrFile`與緩衝區的指標所配置的之後您建構, [CFileDialog](../../mfc/reference/cfiledialog-class.md)，但在呼叫之前`DoModal`。 此外，您必須設定`m_ofn.nMaxFile`所指向的緩衝區中的字元數`m_ofn.lpstrFile`。 如果您設定要選取的檔案數目上限`n`，所需的緩衝區大小是`n`*(_MAX_PATH + 1) + 1。 例如:   
  
 [!code-cpp[NVC_MFCFiles #&23;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_1.cpp)]  
  
 若要讓使用者使用滑鼠或鍵盤調整大小的檔案總管樣式 對話方塊中，設定`OFN_ENABLESIZING`旗標。 只有當您提供的攔截程序或自訂範本，必須設定這個旗標。 旗標僅適用於檔案總管樣式 對話方塊中。無法調整大小的舊式的對話方塊。  
  
 `lpszFilter`參數用來判斷檔案必須在檔案清單中顯示的檔案名稱的型別。 字串組中的第一個字串描述篩選器。第二個字串表示要使用的副檔名。 指定多個延伸模組做為分隔符號使用分號 （';' 字元）。 字串結尾的兩個 ' |' 字元，後面接著`NULL`字元。 您也可以使用[CString](../../atl-mfc-shared/using-cstring.md)這個參數的物件。  
  
 例如，[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]可讓使用者開啟檔案具有副檔名.xlc （圖） 或.xls （工作表） 等等。 Excel 的篩選條件可以寫成︰  
  
 [!code-cpp[NVC_MFCFiles #&24;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_2.cpp)]  
  
 不過，如果您打算使用此字串，以便直接更新`OPENFILENAME`結構，您應該來分隔字串以 null 字元 '\0'，而不是分隔號 ('| ')。  
  
 `bVistaStyle`參數下執行時，才是適用於[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。 在舊版 Windows 中，會忽略此參數。 如果`bVistaStyle`設為`TRUE`，當您編譯的程式[!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)]或更新版本，新的 Vista 樣式**檔案對話方塊**並用。 否則，先前的 MFC 樣式**檔案對話方塊**並用。  
  
 對話方塊範本不支援根據的對話方塊`bVistaStyle`  
  
### <a name="example"></a>範例  
  請參閱範例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namedomodala--cfiledialogdomodal"></a><a name="domodal"></a>CFileDialog::DoModal  
 呼叫此函式來顯示 Windows 通用檔案對話方塊中，並允許使用者瀏覽檔案和目錄，然後輸入檔案名稱。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 **IDOK**或**IDCANCEL**。 如果**IDCANCEL**會傳回，呼叫 Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916)函式來判斷是否發生錯誤。  
  
 **IDOK**和**IDCANCEL**都是常數，指出使用者是否已選取 [確定] 或 [取消] 按鈕。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化的各種不同的檔案對話方塊選項**m_ofn**結構，您應該執行這項操作之前，先呼叫`DoModal`，但在建構對話方塊物件之後。  
  
 例如，如果您想要讓使用者選取多個檔案，設定`OFN_ALLOWMULTISELECT`旗標，然後再呼叫`DoModal`，如本主題中的程式碼範例所示。  
  
 當使用者按一下對話方塊的 [確定] 或 [取消] 按鈕或選取 [關閉選項對話方塊的控制項] 功能表上時，控制傳回到您的應用程式。 您可以再呼叫其他成員函式，來設定或資訊擷取使用者輸入於 對話方塊。  
  
 `DoModal`是從類別中覆寫虛擬函式`CDialog`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&25;](../../atl-mfc-shared/reference/codesnippet/cpp/cfiledialog-class_3.cpp)]  
  
##  <a name="a-nameenableopendropdowna--cfiledialogenableopendropdown"></a><a name="enableopendropdown"></a>CFileDialog::EnableOpenDropDown  
 可讓下拉式清單，在開啟或儲存對話方塊中的按鈕。  
  
```  
HRESULT EnableOpenDropDown(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 下拉式清單的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameendvisualgroupa--cfiledialogendvisualgroup"></a><a name="endvisualgroup"></a>CFileDialog::EndVisualGroup  
 加入的項目 對話方塊中的視覺化群組就會停止。  
  
```  
HRESULT EndVisualGroup();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 S_OK，如果登錄成功。否則為錯誤值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcheckbuttonstatea--cfiledialoggetcheckbuttonstate"></a><a name="getcheckbuttonstate"></a>CFileDialog::GetCheckButtonState  
 擷取對話方塊中的核取按鈕 （核取方塊） 的目前狀態。  
  
```  
HRESULT GetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL& bChecked);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 核取方塊的識別碼。  
  
 `bChecked`  
 核取方塊的狀態。 `TRUE`表示已檢查。`FALSE`表示未核取。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcontrolitemstatea--cfiledialoggetcontrolitemstate"></a><a name="getcontrolitemstate"></a>CFileDialog::GetControlItemState  
 擷取項目 對話方塊中找到的容器控制項中的目前狀態。  
  
```  
HRESULT GetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 項目的識別碼。  
  
 `dwState`  
 多個值的其中一個接收從 CDCONTROLSTATE 列舉，指出控制項的目前狀態的變數參考。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcontrolstatea--cfiledialoggetcontrolstate"></a><a name="getcontrolstate"></a>CFileDialog::GetControlState  
 擷取目前的可見性，並啟用指定的控制項的狀態。  
  
```  
HRESULT GetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF& dwState);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 控制項的 ID。  
  
 `dwState`  
 接收從 CDCONTROLSTATE 列舉，指出控制項的目前狀態的一或多個值的變數參考。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegeteditboxtexta--cfiledialoggeteditboxtext"></a><a name="geteditboxtext"></a>CFileDialog::GetEditBoxText  
 擷取目前的編輯方塊控制項中的文字。  
  
```  
HRESULT GetEditBoxText(
    DWORD dwIDCtl,  
    CString& strText);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 編輯方塊的識別碼。  
  
 `strText`  
 文字值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetfileexta--cfiledialoggetfileext"></a><a name="getfileext"></a>CFileDialog::GetFileExt  
 呼叫此函式可擷取輸入到對話方塊中的檔名的副檔名。  
  
```  
CString GetFileExt() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔名的副檔名。  
  
### <a name="remarks"></a>備註  
 例如，如果輸入檔案的名稱是資料。TXT，`GetFileExt`傳回"TXT"。  
  
 如果`m_ofn.Flags`有`OFN_ALLOWMULTISELECT`設定旗標，這個字串包含一連串的 null 終止的字串，以及所選取的檔案群組的目錄路徑的第一個字串後面的所有使用者所選取的檔案名稱。 若要擷取檔案的路徑名稱，請使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成員函式。  
  
##  <a name="a-namegetfilenamea--cfiledialoggetfilename"></a><a name="getfilename"></a>CFileDialog::GetFileName  
 呼叫此函式來擷取檔名，對話方塊中輸入的名稱。  
  
```  
CString GetFileName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的檔名。  
  
### <a name="remarks"></a>備註  
 檔案名稱包含前置詞和延伸模組。 例如，`GetFileName`會傳回"文字。DAT"C:\FILES\TEXT.DAT 檔案。  
  
 如果`m_ofn.Flags`有`OFN_ALLOWMULTISELECT`旗標設，您應該呼叫[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)擷取檔案的路徑名稱。  
  
##  <a name="a-namegetfiletitlea--cfiledialoggetfiletitle"></a><a name="getfiletitle"></a>CFileDialog::GetFileTitle  
 呼叫此函式可擷取的檔案對話方塊中輸入標題。  
  
```  
CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的標題。  
  
### <a name="remarks"></a>備註  
 檔案的標題包括僅其前置詞，而不需要路徑或擴充功能。 例如，`GetFileTitle`會傳回 「 文字 」 檔案 C:\FILES\TEXT.DAT。  
  
 如果`m_ofn.Flags`有`OFN_ALLOWMULTISELECT`設定旗標，這個字串包含一連串的 null 終止的字串，以及所選取的檔案群組的目錄路徑的第一個字串後面的所有使用者所選取的檔案名稱。 基於這個理由，使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成員函式來擷取清單中的下一個檔案名稱。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namegetfolderpatha--cfiledialoggetfolderpath"></a><a name="getfolderpath"></a>CFileDialog::GetFolderPath  
 呼叫此成員函式，以擷取目前開啟的資料夾或檔案總管樣式開啟] 或 [另存新檔通用的對話方塊中的目錄路徑。  
  
```  
CString GetFolderPath() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含目前開啟的資料夾或目錄。  
  
### <a name="remarks"></a>備註  
 對話方塊中，必須已建立**OFN_EXPLORER**樣式; 否則方法將會失敗，並判斷提示。  
  
 只有當顯示對話方塊時，您可以呼叫這個方法。 在關閉對話方塊之後，無法再使用這個功能，以及方法會判斷提示失敗。  
  
##  <a name="a-namegetifiledialogcustomizea--cfiledialoggetifiledialogcustomize"></a><a name="getifiledialogcustomize"></a>CFileDialog::GetIFileDialogCustomize  
 擷取的內部 COM 物件的指標指定[CFileDialog](../../mfc/reference/cfiledialog-class.md)。  
  
```  
IFileDialogCustomize* GetIFileDialogCustomize();
```  
  
### <a name="return-value"></a>傳回值  
 內部的 COM 物件的指標`CFileDialog`。 您必須負責適當地釋放這個指標。  
  
### <a name="remarks"></a>備註  
 使用此函式只能在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]物件具有`bVistaStyle`設為`true`。 如果您使用此函式時`bVistaStyle`是`false`，它會傳回`NULL`在發行模式和偵錯模式中的判斷提示會擲回。  
  
 如需詳細資訊`IFileDialogCustomize`介面，請參閱[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
### <a name="example"></a>範例  
 此範例會擷取內部的 COM 物件。 若要執行這個程式碼範例，您必須編譯在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&4;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_4.cpp)]  
  
##  <a name="a-namegetifileopendialoga--cfiledialoggetifileopendialog"></a><a name="getifileopendialog"></a>CFileDialog::GetIFileOpenDialog  
 擷取的內部 COM 物件的指標指定`CFileDialog`。  
  
```  
IFileOpenDialog* GetIFileOpenDialog();
```  
  
### <a name="return-value"></a>傳回值  
 內部的 COM 物件的指標`CFileDialog`。 您必須負責適當地釋放這個指標。  
  
### <a name="remarks"></a>備註  
 使用此函式只能在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]物件具有`bVistaStyle`設為`true`。 此函數會傳回`NULL`如果`CFileDialog`不**開啟**對話方塊或是`bVistaStyle`設為`false`。 在這個最後的情況下，函式只會傳回`NULL`在發行模式-偵錯模式則會擲回判斷提示。  
  
 如需詳細資訊`IFileOpenDialog`介面，請參閱[IFileOpenDialog](http://msdn.microsoft.com/library/windows/desktop/bb775834)。  
  
### <a name="example"></a>範例  
 此範例會擷取內部的 COM 物件。 若要執行此程式碼，您必須編譯在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&2;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_5.cpp)]  
  
##  <a name="a-namegetifilesavedialoga--cfiledialoggetifilesavedialog"></a><a name="getifilesavedialog"></a>CFileDialog::GetIFileSaveDialog  
 擷取的內部 COM 物件的指標指定`CFileDialog`。  
  
```  
IFileSaveDialog* GetIFileSaveDialog();
```  
  
### <a name="return-value"></a>傳回值  
 內部的 COM 物件的指標`CFileDialog`。 您必須負責適當地釋放這個指標。  
  
### <a name="remarks"></a>備註  
 使用此函式只能在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]物件具有`bVistaStyle`設為`true`。 此函式會傳回`NULL`如果`CFileDialog`不**儲存**對話方塊或是`bVistaStyle`設為`false`。 在這個最後的情況下，函式只會傳回`NULL`在發行模式-偵錯模式則會擲回判斷提示。  
  
 如需詳細資訊`IFileSaveDialog`介面，請參閱[IFileSaveDialog](http://msdn.microsoft.com/library/windows/desktop/bb775688)。  
  
### <a name="example"></a>範例  
 此範例會擷取內部的 COM 物件。 若要執行這個程式碼範例，您必須編譯在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&3;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_6.cpp)]  
  
##  <a name="a-namegetnextpathnamea--cfiledialoggetnextpathname"></a><a name="getnextpathname"></a>CFileDialog::GetNextPathName  
 呼叫此函式可擷取在對話方塊中選取群組中的下一個檔名。  
  
```  
CString GetNextPathName(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 參考**位置**前一個傳回值`GetNextPathName`或`GetStartPosition`函式呼叫。 **NULL**如果已經到達清單的結尾。  
  
### <a name="return-value"></a>傳回值  
 檔案的完整路徑。  
  
### <a name="remarks"></a>備註  
 檔名的路徑中包含檔案的標題，再加上的整個目錄路徑。 例如，`GetNextPathName`會傳回 「 C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 檔案。 您可以使用`GetNextPathName`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetStartPosition`。  
  
 如果選取範圍包含一個檔案，則會傳回該檔案名稱。  
  
##  <a name="a-namegetofna--cfiledialoggetofn"></a><a name="getofn"></a>CFileDialog::GetOFN  
 擷取相關聯**OPENFILENAME**結構。  
  
```  
const OPENFILENAME& GetOFN() const;  
  
OPENFILENAME& GetOFN();
```  
  
### <a name="return-value"></a>傳回值  
 [OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構。  
  
### <a name="remarks"></a>備註  
 使用此函式的第二個版本來初始化的外觀**開啟舊檔**或**檔案另存新檔**對話方塊建構後，但它會顯示`DoModal`成員函式。 例如，您可以設定**lpstrTitle**成員**m_ofn**標題要擁有對話方塊。  
  
##  <a name="a-namegetpathnamea--cfiledialoggetpathname"></a><a name="getpathname"></a>CFileDialog::GetPathName  
 呼叫此函式可擷取在對話方塊中輸入檔案的完整路徑。  
  
```  
CString GetPathName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 檔案的完整路徑。  
  
### <a name="remarks"></a>備註  
 檔名的路徑中包含檔案的標題，再加上的整個目錄路徑。 例如，`GetPathName`會傳回 「 C:\FILES\TEXT。DAT"C:\FILES\TEXT.DAT 檔案。  
  
 如果`m_ofn.Flags`有`OFN_ALLOWMULTISELECT`設定旗標，這個字串包含一連串的 null teminated 字串，以及所選取的檔案群組的目錄路徑的第一個字串後面的所有使用者所選取的檔案名稱。 基於這個理由，使用[GetStartPosition](#getstartposition)和[GetNextPathName](#getnextpathname)成員函式來擷取清單中的下一個檔案名稱。  
  
### <a name="example"></a>範例  
  請參閱範例[CFileDialog::DoModal](#domodal)。  
  
##  <a name="a-namegetreadonlyprefa--cfiledialoggetreadonlypref"></a><a name="getreadonlypref"></a>CFileDialog::GetReadOnlyPref  
 呼叫此函式可判斷是否已在 Windows 標準開啟檔案和檔案另存新檔對話方塊中選取 [唯讀] 核取方塊。  
  
```  
BOOL GetReadOnlyPref() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零如果選取唯讀核取方塊 對話方塊中。否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以隱藏 [唯讀] 核取方塊，藉由設定`OFN_HIDEREADONLY`中設定樣式`CFileDialog`建構函式。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式`CFileDialog`物件並不支援此函式。 嘗試使用這個函式[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式`CFileDialog`將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。   
  
##  <a name="a-namegetresulta--cfiledialoggetresult"></a><a name="getresult"></a>CFileDialog::GetResult  
 擷取在對話方塊中的使用者所做的選擇。  
  
```  
IShellItem* GetResult() throw();
```  
  
### <a name="return-value"></a>傳回值  
 代表使用者的選擇 IShellItem 指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetresultsa--cfiledialoggetresults"></a><a name="getresults"></a>CFileDialog::GetResults  
 擷取在對話方塊中，可讓多個選取的使用者的選擇。  
  
```  
IShellItemArray* GetResults() throw();
```  
  
### <a name="return-value"></a>傳回值  
 透過此對話方塊中選取的項目都可以存取 IShellItemArray 指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetselectedcontrolitema--cfiledialoggetselectedcontrolitem"></a><a name="getselectedcontrolitem"></a>CFileDialog::GetSelectedControlItem  
 從指定的容器控制項在對話方塊中，擷取特定項目。  
  
```  
HRESULT GetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD& dwIDItem);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 使用者控制項中選取的項目識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetstartpositiona--cfiledialoggetstartposition"></a><a name="getstartposition"></a>CFileDialog::GetStartPosition  
 呼叫此成員函式擷取的第一個檔案路徑名稱的位置，在清單中，如果`m_ofn.Flags`有`OFN_ALLOWMULTISELECT`旗標設。  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目。**NULL**如果清單是空的。  
  
##  <a name="a-namehidecontrola--cfiledialoghidecontrol"></a><a name="hidecontrol"></a>CFileDialog::HideControl  
 呼叫此成員函式，若要隱藏在檔案總管樣式開啟] 或 [另存新檔通用的對話方塊中指定的控制項。  
  
```  
void HideControl(int nID);
```  
  
### <a name="parameters"></a>參數  
 `nID`  
 若要隱藏控制項的 ID。  
  
### <a name="remarks"></a>備註  
 對話方塊中，必須已建立**OFN_EXPLORER**樣式; 否則函式會失敗，並判斷提示。  
  
##  <a name="a-nameispickfoldersmodea--cfiledialogispickfoldersmode"></a><a name="ispickfoldersmode"></a>CFileDialog::IsPickFoldersMode  
 判斷目前的對話方塊是否在資料夾選擇器模式。  
  
```  
BOOL IsPickFoldersMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果對話方塊位於資料夾選擇器模式。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemofna--cfiledialogmofn"></a><a name="m_ofn"></a>CFileDialog::m_ofn  
 `m_ofn`是一種型別的結構`OPENFILENAME`。 此結構中的資料表示的目前狀態`CFileDialog`。  
  
### <a name="remarks"></a>備註  
 使用此結構來初始化的外觀**開啟舊檔**或**檔案另存新檔**對話方塊建構它後，但您將其與顯示[DoModal](#domodal)方法。 例如，您可以設定`lpstrTitle`成員`m_ofn`標題要擁有對話方塊。  
  
 使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式[CFileDialog](../../mfc/reference/cfiledialog-class.md)，`m_ofn`不保證一定要相符 對話方塊中的狀態。 它是在舊版 Windows 中的對話方塊與同步處理。 請參閱[CFileDialog::ApplyOFNToShellDialog](#applyofntoshelldialog)和[CFileDialog::UpdateOFNFromShellDialog](#updateofnfromshelldialog)如需有關同步處理`m_ofn`結構和`CFileDialog`狀態下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]。  
  
 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式的檔案對話方塊不支援某些成員和旗標的`CFileDialog`。 如此一來，這些會有任何作用。  
  
 以下是不支援成員的清單[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]:  
  
- `lpstrCustomFilter`  
  
- `lpstrInitialDir`  
  
- `lCustData`  
  
- `lpfnHook`  
  
- `lpTemplateName`  
  
 不支援下列旗標，也因此沒有任何作用，當您使用[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式`CFileDialog`:  
  
-   OFN_ENABLEHOOK  
  
-   OFN_ENABLEINCLUDENOTIFY  
  
-   OFN_ENABLETEMPLATE  
  
-   OFN_ENABLETEMPLATEHANDLE  
  
-   OFN_EXPLORER  
  
-   OFN_EXTENSIONDIFFERENT  
  
-   OFN_HIDEREADONLY  
  
-   OFN_LONGNAMES-永遠有效上中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NOLONGNAMES-實際上永遠關閉中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_NONETWORKBUTTON-永遠有效上中[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]  
  
-   OFN_READONLY  
  
-   OFN_SHOWHELP  
  
 如需此結構的詳細資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemakeprominenta--cfiledialogmakeprominent"></a><a name="makeprominent"></a>CFileDialog::MakeProminent  
 上的芳鄰 對話方塊中的控制項，讓它突出相較於其他控制項。  
  
```  
HRESULT MakeProminent(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 控制項的 ID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonbuttonclickeda--cfiledialogonbuttonclicked"></a><a name="onbuttonclicked"></a>CFileDialog::OnButtonClicked  
 按一下按鈕時呼叫。  
  
```  
virtual void OnButtonClicked(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 按鈕的 ID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncheckbuttontoggleda--cfiledialogoncheckbuttontoggled"></a><a name="oncheckbuttontoggled"></a>CFileDialog::OnCheckButtonToggled  
 選取或取消選取核取方塊時呼叫。  
  
```  
virtual void OnCheckButtonToggled(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 核取方塊的識別碼。  
  
 `bChecked`  
 選取或取消選取。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameoncontrolactivatinga--cfiledialogoncontrolactivating"></a><a name="oncontrolactivating"></a>CFileDialog::OnControlActivating  
 啟動控制項時呼叫。  
  
```  
virtual void OnControlActivating(DWORD dwIDCtl);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 控制項的 ID。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonfilenamechangea--cfiledialogonfilenamechange"></a><a name="onfilenamechange"></a>CFileDialog::OnFileNameChange  
 覆寫這個方法，如果您想要處理`WM_NOTIFY``CDN_SELCHANGE`訊息。  
  
```  
virtual void OnFileNameChange();
```  
  
### <a name="remarks"></a>備註  
 系統會傳送`CDN_SELCHANGE`當使用者選取的檔案清單中的新檔案或資料夾時，訊息**開啟**或**另存新檔**對話方塊。 如果您想要執行任何動作以回應這個訊息，請覆寫這個方法。  
  
 只有開啟 OFN_EXPLORER 旗標建立對話方塊時，系統會傳送此訊息。 如需通知的詳細資訊，請參閱[CDN_SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646865)。 OFN_EXPLORER 旗標的相關資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構和[開啟和儲存為對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameonfilenameoka--cfiledialogonfilenameok"></a><a name="onfilenameok"></a>CFileDialog::OnFileNameOK  
 只有在您想要提供自訂驗證的通用檔案對話方塊中輸入的檔名會覆寫這個函式。  
  
```  
virtual BOOL OnFileNameOK();
```  
  
### <a name="return-value"></a>傳回值  
 1，如果檔案不是有效的檔名。否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式可讓您為特定應用程式因故拒絕檔名。 一般來說，您不需要使用此函式，因為架構提供的檔名的預設驗證，並顯示訊息方塊，如果輸入無效的檔名。  
  
 如果傳回 1，則對話方塊中將仍會顯示輸入另一個檔名的使用者。 對話方塊程序解除 [] 對話方塊中，如果傳回 0。 其他非零傳回值是目前保留的不應使用。  
  
##  <a name="a-nameonfolderchangea--cfiledialogonfolderchange"></a><a name="onfolderchange"></a>CFileDialog::OnFolderChange  
 覆寫這個函式來處理**WM_NOTIFYCDN_FOLDERCHANGE**訊息。  
  
```  
virtual void OnFolderChange();
```  
  
### <a name="remarks"></a>備註  
 [開啟] 或 [另存新檔] 對話方塊中開啟新的資料夾時，會傳送通知訊息。  
  
 只有具有 OFN_EXPLORER 樣式建立對話方塊時，會傳送通知。 如需通知的詳細資訊，請參閱[CDN_FOLDERCHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646859)。 OFN_EXPLORER 樣式的相關資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構和[開啟和儲存為對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameoninitdonea--cfiledialogoninitdone"></a><a name="oninitdone"></a>CFileDialog::OnInitDone  
 覆寫這個函式來處理`WM_NOTIFY``CDN_INITDONE`訊息。  
  
```  
virtual void OnInitDone();
```  
  
### <a name="remarks"></a>備註  
 排列控制項中的完成系統時，系統會傳送這個通知訊息**開啟**或**另存新檔** 對話方塊中，以騰出空間的子系 對話方塊的控制項。  
  
 只有 OFN_EXPLORER 樣式建立對話方塊時，系統會傳送此。 如需通知的詳細資訊，請參閱[CDN_INITDONE](http://msdn.microsoft.com/library/windows/desktop/ms646863)。 OFN_EXPLORER 樣式的相關資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構和[開啟和儲存為對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式的檔案對話方塊不支援此函式。 嘗試使用這個函式[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式檔案對話方塊將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 
  
##  <a name="a-nameonitemselecteda--cfiledialogonitemselected"></a><a name="onitemselected"></a>CFileDialog::OnItemSelected  
 選取的容器項目時呼叫。  
  
```  
virtual void OnItemSelected(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 項目的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonlbselchangednotifya--cfiledialogonlbselchangednotify"></a><a name="onlbselchangednotify"></a>CFileDialog::OnLBSelChangedNotify  
 若要變更清單方塊中目前的選取範圍時，會呼叫此函數。  
  
```  
virtual void OnLBSelChangedNotify(
    UINT nIDBox,  
    UINT iCurSel,  
    UINT nCode);
```  
  
### <a name="parameters"></a>參數  
 *nIDBox*  
 清單方塊或下拉式方塊選取項目發生的識別碼。  
  
 `iCurSel`  
 在目前選取的索引。  
  
 `nCode`  
 控制項告知程式碼。 這個參數必須具有下列值之一︰  
  
- **CD_LBSELCHANGE**指定`iCurSel`是單一選取清單方塊中選取的項目。  
  
- **CD_LBSELSUB**指定`iCurSel`不再被選取多重選取清單方塊中。  
  
- **CD_LBSELADD**指定`iCurSel`多重選取清單方塊中選取。  
  
- **CD_LBSELNOITEMS**沒有選取項目存在多重選取清單方塊中指定。  
  
### <a name="remarks"></a>備註  
 覆寫此函式可提供的清單方塊中的選取範圍變更的自訂處理。 例如，您可以使用此函式，若要顯示的存取權限，或日期的上次修改每個檔案的使用者選取。  
  
##  <a name="a-nameonshareviolationa--cfiledialogonshareviolation"></a><a name="onshareviolation"></a>CFileDialog::OnShareViolation  
 覆寫這個函式，以提供自訂處理共用違規。  
  
```  
virtual UINT OnShareViolation(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>參數  
 `lpszPathName`  
 發生共用違規的檔案路徑。  
  
### <a name="return-value"></a>傳回值  
 下列其中一個值：  
  
- **OFN_SHAREFALLTHROUGH**從對話方塊傳回檔案名稱。  
  
- **OFN_SHARENOWARN**需要採取任何進一步的動作。  
  
- **OFN_SHAREWARN**使用者會收到這個錯誤的標準的警告訊息。  
  
### <a name="remarks"></a>備註  
 一般來說，您不需要使用此函式，因為架構提供預設的共用違規檢查，並顯示訊息方塊，如果發生共用違規。  
  
 如果您想要停用共用違規檢查，則使用位元 OR 運算子來結合旗標**OFN_SHAREAWARE**與`m_ofn.Flags`。  
  
##  <a name="a-nameontypechangea--cfiledialogontypechange"></a><a name="ontypechange"></a>CFileDialog::OnTypeChange  
 覆寫這個函式來處理**WM_NOTIFYCDN_TYPECHANGE**訊息。  
  
```  
virtual void OnTypeChange();
```  
  
### <a name="remarks"></a>備註  
 當使用者選取新檔案類型從清單中開啟的檔案類型或另存新檔 對話方塊中，會傳送通知訊息。  
  
 只有具有 OFN_EXPLORER 樣式建立對話方塊時，會傳送通知。 如需通知的詳細資訊，請參閱[CDN_TYPECHANGE](http://msdn.microsoft.com/library/windows/desktop/ms646868)。 OFN_EXPLORER 樣式的相關資訊，請參閱[OPENFILENAME](http://msdn.microsoft.com/library/windows/desktop/ms646839)結構和[開啟和儲存為對話方塊](http://msdn.microsoft.com/library/windows/desktop/ms646960)。  
  
##  <a name="a-nameremovecontrolitema--cfiledialogremovecontrolitem"></a><a name="removecontrolitem"></a>CFileDialog::RemoveControlItem  
 在對話方塊中的容器控制項中移除的項目。  
  
```  
HRESULT RemoveControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 要移除的項目從容器控制項的識別碼。  
  
 `dwIDItem`  
 項目的識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcheckbuttonstatea--cfiledialogsetcheckbuttonstate"></a><a name="setcheckbuttonstate"></a>CFileDialog::SetCheckButtonState  
 在對話方塊中設定的核取按鈕 （核取方塊） 的目前狀態。  
  
```  
HRESULT SetCheckButtonState(
    DWORD dwIDCtl,  
    BOOL bChecked);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 核取方塊的識別碼。  
  
 `bChecked`  
 核取方塊的狀態。 `TRUE`表示已檢查。`FALSE`表示未核取。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcontrolitemstatea--cfiledialogsetcontrolitemstate"></a><a name="setcontrolitemstate"></a>CFileDialog::SetControlItemState  
 在對話方塊中找到的容器控制項中設定項目的目前狀態。  
  
```  
HRESULT SetControlItemState(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 項目的識別碼。  
  
 `dwState`  
 一或多個值從 CDCONTROLSTATE 列舉，指出控制項的新狀態。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcontrolitemtexta--cfiledialogsetcontrolitemtext"></a><a name="setcontrolitemtext"></a>CFileDialog::SetControlItemText  
 設定控制項項目的文字。 例如，文字所附的選項按鈕或功能表項目。  
  
```  
HRESULT SetControlItemText(
    DWORD dwIDCtl,  
    DWORD dwIDItem,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 項目的識別碼。  
  
 `strLabel`  
 項目的文字。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcontrollabela--cfiledialogsetcontrollabel"></a><a name="setcontrollabel"></a>CFileDialog::SetControlLabel  
 設定按鈕文字或編輯標籤等控制項，與相關聯的文字。  
  
```  
HRESULT SetControlLabel(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 控制項的 ID。  
  
 `strLabel`  
 控制項名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcontrolstatea--cfiledialogsetcontrolstate"></a><a name="setcontrolstate"></a>CFileDialog::SetControlState  
 設定目前的可見性，並啟用指定的控制項的狀態。  
  
```  
HRESULT SetControlState(
    DWORD dwIDCtl,  
    CDCONTROLSTATEF dwState);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 控制項的 ID。  
  
 `dwState`  
 一或多個值從 CDCONTROLSTATE 列舉，指出控制項的目前狀態。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetcontroltexta--cfiledialogsetcontroltext"></a><a name="setcontroltext"></a>CFileDialog::SetControlText  
 呼叫這個方法，在檔案總管樣式設定為指定的控制項文字**開啟**或**另存新檔**對話方塊。  
  
```  
void SetControlText(
    int nID,  
    LPCSTR lpsz);

 
void SetControlText(
    int nID,  
    const wchar_t *lpsz);
```  
  
### <a name="parameters"></a>參數  
 [in] `nID`  
 若要設定文字的控制項 ID。  
  
 [in] `lpsz`  
 包含要設定控制項的文字字串的指標。  
  
### <a name="remarks"></a>備註  
 此函式的兩個版本都有效使用 Unicode 的應用程式。 但是，使用 LPCSTR 類型的版本是有效的應用程式使用[!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)]。  
  
 若要使用這個方法，您必須建立對話方塊 OFN_EXPLORER 樣式。 否則，函式會失敗，並判斷提示。  
  
##  <a name="a-namesetdefexta--cfiledialogsetdefext"></a><a name="setdefext"></a>CFileDialog::SetDefExt  
 呼叫此函式可設定 檔案總管樣式開啟 或 另存新檔通用的對話方塊中的預設檔案名稱副檔名。  
  
```  
void SetDefExt(LPCSTR lpsz);
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 包含要用於對話方塊物件的預設副檔名字串的指標。 這個字串不能包含句號 （.）。  
  
### <a name="remarks"></a>備註  
 對話方塊中，必須已建立**OFN_EXPLORER**樣式; 否則函式會失敗，並判斷提示。  
  
##  <a name="a-nameseteditboxtexta--cfiledialogseteditboxtext"></a><a name="seteditboxtext"></a>CFileDialog::SetEditBoxText  
 設定目前的文字編輯方塊控制項中。  
  
```  
HRESULT SetEditBoxText(
    DWORD dwIDCtl,  
    const CString& strText);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 編輯方塊的識別碼。  
  
 `strText`  
 文字值。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetpropertiesa--cfiledialogsetproperties"></a><a name="setproperties"></a>CFileDialog::SetProperties  
 提供屬性儲存區，可定義要用於所儲存之項目的預設值。  
  
```  
BOOL SetProperties(LPCWSTR lpszPropList);
```  
  
### <a name="parameters"></a>參數  
 `lpszPropList`  
 預先定義的屬性清單，以 ";" 分隔。 如需旗標的清單，請參閱`Flags`區段[OPENFILENAME](http://msdn.microsoft.com/en-us/8cecfd45-f7c1-4f8d-81a0-4e7fecc3b104)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetselectedcontrolitema--cfiledialogsetselectedcontrolitem"></a><a name="setselectedcontrolitem"></a>CFileDialog::SetSelectedControlItem  
 選項按鈕群組或在對話方塊中找到下拉式方塊中設定特定項目的選取的狀態。  
  
```  
HRESULT SetSelectedControlItem(
    DWORD dwIDCtl,  
    DWORD dwIDItem);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 容器控制項的 ID。  
  
 `dwIDItem`  
 使用者控制項中選取的項目識別碼。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesettemplatea--cfiledialogsettemplate"></a><a name="settemplate"></a>CFileDialog::SetTemplate  
 設定的對話方塊範本[CFileDialog](../../mfc/reference/cfiledialog-class.md)物件。  
  
```  
void SetTemplate(
    UINT nWin3ID,  
    UINT nWin4ID);

 
void SetTemplate(
    LPCTSTR lpWin3ID,  
    LPCTSTR lpWin4ID);
```  
  
### <a name="parameters"></a>參數  
 [in] `nWin3ID`  
 包含非 Explorer 的範本資源的 ID 編號`CFileDialog`物件。 這個範本只會在 Windows NT 3.51 或 OFN_EXPLORER 樣式不存在。  
  
 [in] `nWin4ID`  
 檔案總管中包含的範本資源的 ID 編號`CFileDialog`物件。 此範本僅適用於[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更新版本、 Windows 95 和更新版本中，或存在 OFN_EXPLORER 樣式時。  
  
 [in] `lpWin3ID`  
 包含非 Explorer 範本資源名稱`CFileDialog`物件。 這個範本只會在 Windows NT 3.51 或 OFN_EXPLORER 樣式不存在。  
  
 [in] `lpWin4ID`  
 包含名稱的 [總管] 中的範本資源`CFileDialog`物件。 此範本僅適用於[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更新版本、 Windows 95 和更新版本中，或存在 OFN_EXPLORER 樣式時。  
  
### <a name="remarks"></a>備註  
 系統會使用其中一個指定的範本。 系統會決定要使用哪一個範本根據 OFN_EXPLORER 樣式和作業系統上執行應用程式存在。 藉由指定的非總管 」 和 「 檔案總管樣式範本，很容易支援 Windows NT 3.51[!INCLUDE[WinNt4Family](../../mfc/reference/includes/winnt4family_md.md)]和更新版本中，Windows 95 和更新版本。  
  
> [!NOTE]
> [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式 [檔案] 對話方塊不支援此函式。 嘗試使用這個函式[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]樣式 [檔案] 對話方塊將會擲回[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。 替代方法是使用自訂的對話方塊。 如需有關使用自訂`CFileDialog`，請參閱[IFileDialogCustomize](http://msdn.microsoft.com/library/windows/desktop/bb775912)。  
  
##  <a name="a-namestartvisualgroupa--cfiledialogstartvisualgroup"></a><a name="startvisualgroup"></a>CFileDialog::StartVisualGroup  
 宣告可見的群組，在對話方塊中。 任何 「 加入 」 方法的後續呼叫會將這些項目新增至此群組。  
  
```  
HRESULT StartVisualGroup(
    DWORD dwIDCtl,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>參數  
 `dwIDCtl`  
 視覺化群組的識別碼。  
  
 `strLabel`  
 群組名稱。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameupdateofnfromshelldialoga--cfiledialogupdateofnfromshelldialog"></a><a name="updateofnfromshelldialog"></a>CFileDialog::UpdateOFNFromShellDialog  
 更新`m_ofn`資料結構[CFileDialog](../../mfc/reference/cfiledialog-class.md)根據內部物件的目前狀態。  
  
```  
void UpdateOFNFromShellDialog();
```  
  
### <a name="remarks"></a>備註  
 在之前的 Windows 版本[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，成員[OPENFILENAME](https://msdn.microsoft.com/library/ms911906.aspx)連續資料結構進行同步處理的狀態`CFileDialog`。 任何對[m_ofn](#m_ofn)成員變數的直接影響 對話方塊中的狀態。 此外，任何在對話方塊的狀態變更會立即更新 m_ofn 成員變數。  
  
 在[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]、`m_ofn`資料結構不會自動更新。 若要保證中資料的正確性`m_ofn`成員變數，您應該呼叫`UpdateOFNFromShellDialog`函式，才能存取資料。 Windows 會呼叫此函數會自動在處理期間[IFileDialog::OnFileOK](http://msdn.microsoft.com/library/windows/desktop/bb775879)。  
  
 如需有關如何使用`CFileDialog`類別下[!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]，請參閱[CFileDialog 類別](../../mfc/reference/cfiledialog-class.md)。  
  
### <a name="example"></a>範例  
 這個範例會更新`CFileDialog`之前顯示。 在更新之前`m_ofn`成員變數中，我們需要進行同步處理 對話方塊中的目前狀態。  
  
 [!code-cpp[NVC_MFC_CFileDialog #&1;](../../mfc/reference/codesnippet/cpp/cfiledialog-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CCommonDialog 類別](../../mfc/reference/ccommondialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


