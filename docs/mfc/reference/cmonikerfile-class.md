---
title: CMonikerFile 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 431e743396cfc22d49c13a2a9e2f50c88c5ee036
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369225"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 類別
表示資料的資料流 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) 名為[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|建構 `CMonikerFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|卸離並釋放資料流並釋放 moniker。|  
|[CMonikerFile::Detach](#detach)|卸離`IMoniker`從此`CMonikerFile`物件。|  
|[CMonikerFile::GetMoniker](#getmoniker)|傳回目前的 moniker。|  
|[CMonikerFile::Open](#open)|開啟指定的檔案取得資料流。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|取得繫結內容，或建立的預設值初始化繫結內容。|  
  
## <a name="remarks"></a>備註  
 Moniker 包含非常類似檔案的路徑名稱的資訊。 如果您有 moniker 物件的指標`IMoniker`介面，可以取得已識別檔案的存取權，而不需要任何其他特定相關檔案所在位置實際資訊。  
  
 衍生自`COleStreamFile`，`CMonikerFile`取得 moniker 或者可以製作成 moniker 的字串表示法，並繫結至資料流 moniker 的名稱。 您可以讀取並寫入該資料流。 實際用途`CMonikerFile`是提供簡單的存取權`IStream`s 命名`IMoniker`s，讓您不必自己繫結至資料流，尚未擁有`CFile`資料流的功能。  
  
 `CMonikerFile` 不能繫結至資料流以外的任何項目。 如果您想要繫結至儲存體或物件，您必須使用`IMoniker`直接介面。  
  
 如需有關資料流和 moniker 的詳細資訊，請參閱[COleStreamFile](../../mfc/reference/colestreamfile-class.md)中*MFC 參考*和[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)中Windows SDK。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxole.h  
  
##  <a name="close"></a>  CMonikerFile::Close  
 呼叫此函式來卸離，並釋放資料流，並釋放 moniker。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 可以在未開啟或已關閉的資料流上呼叫。  
  
##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile  
 建構 `CMonikerFile` 物件。  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext  
 呼叫此函式來建立預設值初始化繫結內容。  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>參數  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，它就會設定為可能的原因。  
  
### <a name="return-value"></a>傳回值  
 繫結內容的指標[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)要與繫結，如果成功，否則**NULL**。 如果執行個體以開啟`IBindHost`介面，繫結內容擷取從`IBindHost`。 如果沒有任何`IBindHost`介面或介面無法傳回繫結內容、 繫結內容建立。 如需說明的[IBindHost](http://msdn.microsoft.com/library/ie/ms775076)介面，請參閱 Windows SDK。  
  
### <a name="remarks"></a>備註  
 繫結內容是儲存在特定的 moniker 繫結作業的相關資訊的物件。 您可以覆寫此函式可提供自訂的繫結內容。  
  
##  <a name="detach"></a>  CMonikerFile::Detach  
 呼叫此函式來關閉資料流。  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，它就會設定為可能的原因。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker  
 呼叫此函式可擷取目前 moniker 的指標。  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的 moniker 介面的指標 ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705))。  
  
### <a name="remarks"></a>備註  
 因為`CMonikerFile`不是介面，傳回的指標不會遞增參考計數 (透過[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379))，並釋放 moniker 時`CMonikerFile`釋放物件。 如果您想要保留 moniker 或自行發行，您必須`AddRef`它。  
  
##  <a name="open"></a>  CMonikerFile::Open  
 呼叫此成員函式，以開啟檔案或 moniker 物件。  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszURL`  
 URL 或開啟檔案的檔案名稱。  
  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，它就會設定為可能的原因。  
  
 `pMoniker`  
 Moniker 介面的指標`IMoniker`用來取得資料流。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `lpszURL`參數不能在 Macintosh。 只有`pMoniker`形式**開啟**可以用於 Macintosh。  
  
 您可以使用 URL 或檔案名稱`lpszURL`參數。 例如:   
  
 [!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleStreamFile 類別](../../mfc/reference/colestreamfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
