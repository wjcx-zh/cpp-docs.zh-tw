---
title: "COleDataObject 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDataObject
- COleDataObject
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject interface, MFC encapsulation
- data transfer [C++]
- data transfer [C++], OLE
- OLE data transfer [C++]
- COleDataObject class
- uniform data transfer, OLE
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f30ca208252fe81f1e47d9e8f817cb9137656540
ms.lasthandoff: 02/24/2017

---
# <a name="coledataobject-class"></a>COleDataObject 類別
用於資料傳輸以透過剪貼簿、拖放作業或內嵌 OLE 項目擷取各種格式的資料。  
  
## <a name="syntax"></a>語法  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|建構 `COleDataObject` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|附加至指定的 OLE 資料物件`COleDataObject`。|  
|[COleDataObject::AttachClipboard](#attachclipboard)|將剪貼簿上的資料物件。|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|準備一個或多後續`GetNextFormat`呼叫。|  
|[COleDataObject::Detach](#detach)|卸離相關聯`IDataObject`物件。|  
|[COleDataObject::GetData](#getdata)|從附加 OLE 資料物件中指定的格式將資料複製。|  
|[COleDataObject::GetFileData](#getfiledata)|將資料複製到附加的 OLE 資料物件從`CFile`指標指定的格式。|  
|[COleDataObject::GetGlobalData](#getglobaldata)|將資料複製到附加的 OLE 資料物件從`HGLOBAL`中指定的格式。|  
|[COleDataObject::GetNextFormat](#getnextformat)|傳回下一個可用的資料格式。|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|檢查資料是否可以使用指定的格式。|  
|[COleDataObject::Release](#release)|卸離，並釋放相關聯`IDataObject`物件。|  
  
## <a name="remarks"></a>備註  
 `COleDataObject`沒有基底類別。  
  
 這些種類的資料傳輸包括來源和目的地。 資料來源物件的形式實作[COleDataSource](../../mfc/reference/coledatasource-class.md)類別。 每當接收端應用程式放在它的資料，或被要求從剪貼簿中的物件執行貼上作業`COleDataObject`必須建立類別。  
  
 這個類別可讓您判斷資料是否存在於指定的格式。 您可以也列舉可用的資料格式或檢查是否以指定的格式，然後擷取 慣用的格式中的資料。 可以透過幾種不同的方式，包括使用完成物件擷取[CFile](../../mfc/reference/cfile-class.md)、 `HGLOBAL`，或**STGMEDIUM**結構。  
  
 如需詳細資訊，請參閱[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需應用程式中使用資料物件的詳細資訊，請參閱文章[資料物件和資料來源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `COleDataObject`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxole.h  
  
##  <a name="a-nameattacha--coledataobjectattach"></a><a name="attach"></a>COleDataObject::Attach  
 呼叫此函式來建立關聯`COleDataObject`OLE 資料物件的物件。  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *lpDataObject*  
 OLE 資料物件的指標。  
  
 `bAutoRelease`  
 **TRUE**如果應該 OLE 資料物件時釋放`COleDataObject`物件就會終結，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameattachclipboarda--coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 呼叫此函式來附加至剪貼簿上目前的資料物件`COleDataObject`物件。  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  呼叫此函式會鎖定剪貼簿，直到釋放這個資料物件。 資料物件的解構函式在釋放`COleDataObject`。 如需詳細資訊，請參閱[OpenClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649048)和[CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) Win32 文件中。  
  
##  <a name="a-namebeginenumformatsa--coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormats  
 呼叫此函式的後續呼叫準備`GetNextFormat`從項目擷取的資料格式清單。  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>備註  
 若要在呼叫`BeginEnumFormats`，儲存這個資料物件支援的第一個格式的位置。 後續呼叫`GetNextFormat`會列舉資料物件中的可用格式的清單。  
  
 若要檢查的指定格式的資料可用性，請使用[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 如需詳細資訊，請參閱[IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecoledataobjecta--coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject  
 建構 `COleDataObject` 物件。  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>備註  
 呼叫[COleDataObject::Attach](#attach)或[COleDataObject::AttachClipboard](#attachclipboard)必須呼叫其他之前進行`COleDataObject`函式。  
  
> [!NOTE]
>  由於其中一個拖放處理常式的參數是一個指向`COleDataObject`，就不需要呼叫這個建構函式，以支援拖放。  
  
##  <a name="a-namedetacha--coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach  
 呼叫此函式可卸離`COleDataObject`從但未釋放資料物件及其相關聯 OLE 資料物件的物件。  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>傳回值  
 已卸離 OLE 資料物件的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetdataa--coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData  
 呼叫此函式可擷取資料的項目中指定的格式。  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料所要傳回的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)會接收資料的結構。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料所要傳回的格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，預設值使用中的其他欄位**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetfiledataa--coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData  
 呼叫此函式建立`CFile`或`CFile`-衍生物件，以及擷取資料到指定的格式`CFile`指標。  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料所要傳回的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料所要傳回的格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，預設值使用中的其他欄位**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 新指標`CFile`或`CFile`-衍生的物件，其中包含資料，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 傳回的值所指向的實際型別可能會根據資料儲存在媒體， `CFile`， `CSharedFile`，或`COleStreamFile`。  
  
> [!NOTE]
>  `CFile`呼叫端擁有存取此函式的傳回值的物件。 呼叫端負責**刪除**`CFile`物件，藉此關閉檔案。  
  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetglobaldataa--coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 呼叫此函式配置全域記憶體區塊，並擷取資料到指定的格式`HGLOBAL`。  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 資料所要傳回的格式。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述資料所要傳回的格式。 如果您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供的值`cfFormat`。 如果是**NULL**，預設值使用中的其他欄位**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 包含資料成功; 如果全域記憶體區塊的控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnextformata--coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat  
 呼叫此函式重複，以取得所有可用項目從擷取資料的格式。  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>參數  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)函式呼叫傳回時，收到格式資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 另一種格式可使用; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 若要在呼叫[COleDataObject::BeginEnumFormats](#beginenumformats)，儲存這個資料物件支援的第一個格式的位置。 後續呼叫`GetNextFormat`會列舉資料物件中的可用格式的清單。 若要列出可用的格式中使用這些函式。  
  
 若要檢查特定格式的可用性，請呼叫[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 如需詳細資訊，請參閱[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameisdataavailablea--coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::IsDataAvailable  
 呼叫此函式可判斷是否可供 OLE 項目擷取資料的特定格式。  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>參數  
 `cfFormat`  
 使用結構中的剪貼簿資料格式所指`lpFormatEtc`。 這個參數可以是其中一個預先定義的剪貼簿格式或原生 Windows 所傳回的值[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)結構描述所需的格式。 只有當您想要指定其他的格式資訊所指定的剪貼簿格式之外，此參數提供值`cfFormat`。 如果是**NULL**，預設值使用中的其他欄位**FORMATETC**結構。  
  
### <a name="return-value"></a>傳回值  
 資料可在指定的格式; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式可以呼叫之前，先`GetData`， `GetFileData`，或`GetGlobalData`。  
  
 如需詳細資訊，請參閱[IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 如需詳細資訊，請參閱[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)。  
  
##  <a name="a-namereleasea--coledataobjectrelease"></a><a name="release"></a>COleDataObject::Release  
 呼叫此函式釋放的擁有權[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)先前與相關聯的物件`COleDataObject`物件。  
  
```  
void Release();
```  
  
### <a name="remarks"></a>備註  
 `IDataObject`關聯`COleDataObject`藉由呼叫**附加**或`AttachClipboard`明確或架構。 如果`bAutoRelease`參數**附加**是**FALSE**、`IDataObject`將不會釋放物件。 在此情況下，呼叫端負責釋放`IDataObject`藉由呼叫[Iunknown](http://msdn.microsoft.com/library/windows/desktop/ms682317)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDataSource 類別](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem 類別](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem 類別](../../mfc/reference/coleserveritem-class.md)

