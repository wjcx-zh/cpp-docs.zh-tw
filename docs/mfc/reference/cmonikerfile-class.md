---
title: "CMonikerFile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CMonikerFile class
- monikers, MFC
- IMoniker interface, binding
- IMoniker interface
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4668672af1b33170ece1cb4d449ed5a20f6040e7
ms.lasthandoff: 02/24/2017

---
# <a name="cmonikerfile-class"></a>CMonikerFile 類別
表示資料的資料流 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) 由名為[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|建構 `CMonikerFile` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|卸離並釋放資料流，並釋放 moniker。|  
|[CMonikerFile::Detach](#detach)|卸離`IMoniker`從此`CMonikerFile`物件。|  
|[CMonikerFile::GetMoniker](#getmoniker)|傳回目前的 moniker。|  
|[CMonikerFile::Open](#open)|開啟指定的檔案，以取得資料流。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|取得繫結內容，或建立預設值初始化繫結內容。|  
  
## <a name="remarks"></a>備註  
 Moniker 包含檔案的路徑名稱非常類似的資訊。 如果您有 moniker 物件的指標`IMoniker`介面，可讓識別檔案的存取，而不需要任何其他特定資訊檔的位置實際。  
  
 衍生自`COleStreamFile`，`CMonikerFile`取得 moniker 或者可以製作成 moniker 的字串表示，並且會繫結至資料流 moniker 的名稱。 然後讀取及寫入資料流。 真正目的`CMonikerFile`是要提供簡單地存取`IStream`s 命名`IMoniker`s，您不需要將繫結至資料流，還沒有`CFile`資料流的功能。  
  
 `CMonikerFile`不用來繫結至資料流以外的任何項目。 如果您想要繫結至儲存體或物件，您必須使用`IMoniker`直接介面。  
  
 如需有關資料流和 moniker 的詳細資訊，請參閱[COleStreamFile](../../mfc/reference/colestreamfile-class.md)中*MFC 參考*和[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="close"></a>CMonikerFile::Close  
 呼叫此函式來卸離，並釋放資料流和釋放 moniker。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 可以在未開啟或已關閉資料流上呼叫。  
  
##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile  
 建構 `CMonikerFile` 物件。  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext  
 呼叫此函式建立預設值初始化繫結內容。  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>參數  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，它將設定的原因。  
  
### <a name="return-value"></a>傳回值  
 繫結內容的指標[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)要與繫結，如果成功，否則**NULL**。 如果執行個體以開啟`IBindHost`介面，繫結內容擷取從`IBindHost`。 如果沒有任何`IBindHost`介面或介面無法傳回繫結內容，建立繫結內容。 如需說明[IBindHost](http://msdn.microsoft.com/library/ie/ms775076)介面，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 繫結內容是儲存特定 moniker 繫結作業的相關資訊的物件。 您可以覆寫此函式可提供自訂的繫結內容。  
  
##  <a name="detach"></a>CMonikerFile::Detach  
 呼叫此函式來關閉資料流。  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pError`  
 檔案例外狀況的指標。 發生錯誤時，它將設定的原因。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="getmoniker"></a>CMonikerFile::GetMoniker  
 呼叫此函式可擷取目前 moniker 的指標。  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的 moniker 介面的指標 ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705))。  
  
### <a name="remarks"></a>備註  
 由於`CMonikerFile`不是介面，傳回的指標，不會遞增參考計數 (透過[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379))，且放開 moniker 時`CMonikerFile`釋放物件。 如果您想要保留 moniker 或自行發行，您必須`AddRef`它。  
  
##  <a name="open"></a>CMonikerFile::Open  
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
 檔案例外狀況的指標。 發生錯誤時，它將設定的原因。  
  
 `pMoniker`  
 Moniker 介面的指標`IMoniker`用來取得資料流。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `lpszURL`參數不能用在 Macintosh 上。 只有`pMoniker`形式**開啟**可用在 Macintosh 上。  
  
 您可以使用 URL 或檔案名稱`lpszURL`參數。 例如:   
  
 [!code-cpp[NVC_MFCWinInet #&6;](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 -或-  
  
 [!code-cpp[NVC_MFCWinInet #&7;](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [COleStreamFile 類別](../../mfc/reference/colestreamfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)

