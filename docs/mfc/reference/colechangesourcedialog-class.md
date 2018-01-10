---
title: "COleChangeSourceDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
dev_langs: C++
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9eccd25a175479c18a83b5d6ab96753a946e386
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog 類別
用於 OLE 的 [變更來源] 對話方塊。  
  
## <a name="syntax"></a>語法  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|建構 `COleChangeSourceDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[COleChangeSourceDialog::DoModal](#domodal)|顯示 OLE 變更來源 對話方塊。|  
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|取得完整的來源顯示名稱。|  
|[COleChangeSourceDialog::GetFileName](#getfilename)|取得檔案名稱的來源名稱。|  
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|取得上一個來源的前置詞。|  
|[COleChangeSourceDialog::GetItemName](#getitemname)|取得項目名稱的來源名稱。|  
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|取得新的來源的前置詞|  
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|指出來源是否有效。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[COleChangeSourceDialog::m_cs](#m_cs)|結構，控制對話方塊中的行為。|  
  
## <a name="remarks"></a>備註  
 建立類別的物件`COleChangeSourceDialog`當您想要呼叫此對話方塊。 之後`COleChangeSourceDialog`在建構物件，您可以使用[m_cs](#m_cs)結構初始化的值或在對話方塊中控制項的狀態。 `m_cs`結構的類型是[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)。 如需有關如何使用這個對話方塊類別的詳細資訊，請參閱[DoModal](#domodal)成員函式。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) Windows SDK 中的結構。  
  
 如需 OLE 特定對話方塊的詳細資訊，請參閱文章[中 OLE 對話方塊](../../mfc/dialog-boxes-in-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxodlgs.h  
  
##  <a name="colechangesourcedialog"></a>COleChangeSourceDialog::COleChangeSourceDialog  
 此函式會建構`COleChangeSourceDialog`物件。  
  
```  
explicit COleChangeSourceDialog(
    COleClientItem* pItem,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指向連結[COleClientItem](../../mfc/reference/coleclientitem-class.md)更新為其來源。  
  
 `pParentWnd`  
 指向的父系或擁有者的視窗物件 (型別`CWnd`) 所屬之對話方塊物件。 如果是**NULL**，對話方塊中的父視窗將會設定為主要的應用程式視窗。  
  
### <a name="remarks"></a>備註  
 若要顯示的對話方塊，請呼叫[DoModal](#domodal)函式。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)結構和[OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) Windows SDK 中的函式。  
  
##  <a name="domodal"></a>COleChangeSourceDialog::DoModal  
 呼叫此函式可顯示 OLE 變更來源 對話方塊。  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>傳回值  
 對話方塊中的完成狀態。 下列其中一個值：  
  
- **IDOK**如果對話方塊已成功地顯示。  
  
- **IDCANCEL**如果使用者已取消對話方塊。  
  
- **IDABORT**如果發生錯誤。 如果**IDABORT**是傳回，呼叫[COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror)成員函式來取得有關所發生的錯誤類型的詳細資訊。 如需可能的錯誤的清單，請參閱[OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) Windows SDK 中的函式。  
  
### <a name="remarks"></a>備註  
 如果您想要設定的成員初始化各種對話方塊控制項[m_cs](#m_cs)結構，您應該這麼做會在呼叫之前`DoModal`，但在建構對話方塊物件之後。  
  
 如果`DoModal`傳回**IDOK**，您可以呼叫成員函式來擷取從對話方塊中的使用者輸入的設定或資訊。 下列清單名稱一般查詢函式：  
  
- [GetFileName](#getfilename)  
  
- [GetDisplayName](#getdisplayname)  
  
- [GetItemName](#getitemname)  
  
##  <a name="getdisplayname"></a>COleChangeSourceDialog::GetDisplayName  
 呼叫此函式可擷取連結的用戶端項目的完整顯示名稱。  
  
```  
CString GetDisplayName();
```  
  
### <a name="return-value"></a>傳回值  
 完整的來源顯示名稱 (moniker) [COleClientItem](../../mfc/reference/coleclientitem-class.md)建構函式中指定。  
  
##  <a name="getfilename"></a>COleChangeSourceDialog::GetFileName  
 呼叫此函式可擷取檔案 moniker 的部分連結的用戶端項目的顯示名稱。  
  
```  
CString GetFileName();
```  
  
### <a name="return-value"></a>傳回值  
 來源顯示名稱的檔案 moniker 部分[COleClientItem](../../mfc/reference/coleclientitem-class.md)建構函式中指定。  
  
### <a name="remarks"></a>備註  
 項目 moniker 搭配檔案 moniker 提供完整顯示名稱。  
  
##  <a name="getfromprefix"></a>COleChangeSourceDialog::GetFromPrefix  
 呼叫此函式可取得先前的前置詞字串來源。  
  
```  
CString GetFromPrefix();
```  
  
### <a name="return-value"></a>傳回值  
 來源的上一個前置詞字串。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式之後，才[DoModal](#domodal)傳回**IDOK**。  
  
 這個值是直接來自**lpszFrom**隸屬[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)結構。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) Windows SDK 中的結構。  
  
##  <a name="getitemname"></a>COleChangeSourceDialog::GetItemName  
 呼叫此函式可擷取項目 moniker 的部分連結的用戶端項目的顯示名稱。  
  
```  
CString GetItemName();
```  
  
### <a name="return-value"></a>傳回值  
 來源顯示名稱的項目 moniker 部分[COleClientItem](../../mfc/reference/coleclientitem-class.md)建構函式中指定。  
  
### <a name="remarks"></a>備註  
 項目 moniker 搭配檔案 moniker 提供完整顯示名稱。  
  
##  <a name="gettoprefix"></a>COleChangeSourceDialog::GetToPrefix  
 呼叫此函式可取得新的前置詞字串來源。  
  
```  
CString GetToPrefix();
```  
  
### <a name="return-value"></a>傳回值  
 新的前置詞字串的來源。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式之後，才[DoModal](#domodal)傳回**IDOK**。  
  
 這個值是直接來自**lpszTo**隸屬[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)結構。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) Windows SDK 中的結構。  
  
##  <a name="m_cs"></a>COleChangeSourceDialog::m_cs  
 此資料成員是類型的結構[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160)。  
  
```  
OLEUICHANGESOURCE m_cs;  
```  
  
### <a name="remarks"></a>備註  
 `OLEUICHANGESOURCE`用來控制 OLE 變更來源 對話方塊中的行為。 此結構的成員可以直接修改。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) Windows SDK 中的結構。  
  
##  <a name="isvalidsource"></a>COleChangeSourceDialog::IsValidSource  
 呼叫此函式可判斷新的來源是否有效。  
  
```  
BOOL IsValidSource();
```  
  
### <a name="return-value"></a>傳回值  
 新的來源是否有效，則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫這個函式之後，才[DoModal](#domodal)傳回**IDOK**。  
  
 如需詳細資訊，請參閱[OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) Windows SDK 中的結構。  
  
## <a name="see-also"></a>請參閱  
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDialog 類別](../../mfc/reference/coledialog-class.md)
