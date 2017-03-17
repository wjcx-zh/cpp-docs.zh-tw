---
title: "CAtlFileMappingBase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 439f123bc0addbbec2a26102d0197d0a1f14a8d5
ms.lasthandoff: 02/24/2017

---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 類別
此類別代表的記憶體對應檔。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|建構函式。|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|呼叫這個方法來複製檔案對應物件。|  
|[CAtlFileMappingBase::GetData](#getdata)|呼叫這個方法來取得檔案對應物件中的資料。|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|呼叫這個方法傳回的檔案控制代碼。|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|呼叫此方法來取得對應大小從檔案對應物件。|  
|[CAtlFileMappingBase::MapFile](#mapfile)|呼叫這個方法來建立檔案對應物件。|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|呼叫這個方法來建立檔案對應物件，允許所有處理程序的完整存取權。|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|呼叫此方法以傳回檔案對應物件的控制代碼。|  
|[CAtlFileMappingBase::Unmap](#unmap)|呼叫這個方法來取消對應檔案對應物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|設定目前的檔案對應物件到另一個檔案對應物件。|  
  
## <a name="remarks"></a>備註  
 檔案對應是檔案的內容關聯的處理序的虛擬位址空間的一部分。 這個類別會提供用於建立允許程式輕易地存取及共用資料的檔案對應物件的方法。  
  
 如需詳細資訊，請參閱[檔案對應](http://msdn.microsoft.com/library/windows/desktop/aa366556)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase  
 建構函式。  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 若要建立新的物件複製原始的檔案對應物件。  
  
### <a name="remarks"></a>備註  
 建立新的檔案對應物件，您可以選擇使用現有的物件。 仍然必須呼叫[CAtlFileMappingBase::MapFile](#mapfile)開啟或建立特定檔案的檔案對應物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&71;](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 解構函式。  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有資源配置的類別並呼叫[CAtlFileMappingBase::Unmap](#unmap)方法。  
  
##  <a name="copyfrom"></a>CAtlFileMappingBase::CopyFrom  
 呼叫這個方法來複製檔案對應物件。  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 若要從複製原始的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
##  <a name="getdata"></a>CAtlFileMappingBase::GetData  
 呼叫這個方法來取得檔案對應物件中的資料。  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回資料的指標。  
  
##  <a name="gethandle"></a>CAtlFileMappingBase::GetHandle  
 呼叫此方法以傳回檔案對應物件的控制代碼。  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回檔案對應物件的控制代碼。  
  
##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize  
 呼叫此方法來取得對應大小從檔案對應物件。  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回對應的大小。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapfile"></a>CAtlFileMappingBase::MapFile  
 呼叫這個方法來開啟或建立指定之檔案的檔案對應物件。  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>參數  
 `hFile`  
 要建立對應物件的來源檔的控制代碼。 `hFile`必須有效，而且不能設為 INVALID_HANDLE_VALUE。  
  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於目前的識別的檔案大小*hFile。*  
  
 `nOffset`  
 對應是要開始檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 `dwMappingProtection`  
 保護所需要的檔案檢視對應檔。 請參閱`flProtect`中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwViewDesiredAccess`  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 建立檔案對應物件之後，檔案的大小不得超過檔案對應物件中; 的大小如果是的話，不是所有檔案的內容將可供共用。 如需詳細資訊，請參閱[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)和[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 請參閱範例[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem  
 呼叫這個方法來建立檔案對應物件，允許所有處理程序的完整存取權。  
  
```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>參數  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小`szName.`  
  
 `szName`  
 對應物件的名稱。  
  
 *pbAlreadyExisted*  
 指向 BOOL 值設為 TRUE 如果對應的物件已經存在。  
  
 `lpsa`  
 將指標**ATTRIBUTES**結構，決定子處理序是否可以繼承傳回的控制代碼。 請參閱*lpAttributes*中[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwMappingProtection`  
 保護所需要的檔案檢視中，對應檔。 請參閱`flProtect`中**CreateFileMapping**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwViewDesiredAccess`  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 **MapShareMem**可讓現有的檔案對應物件，由[CreateFileMapping](http://msdn.microsoft.com/library/windows/desktop/aa366537)，以處理序之間共用。  
  
##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping  
 呼叫這個方法，以開啟具名的檔案對應物件，為指定的檔案。  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>參數  
 `szName`  
 對應物件的名稱。 如果這個名稱的檔案對應物件的開啟控制代碼，且對應物件的安全性描述元沒有與衝突`dwViewDesiredAccess`參數，開啟作業成功。  
  
 `nMappingSize`  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小`szName.`  
  
 `nOffset`  
 對應是要開始檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 `dwViewDesiredAccess`  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱`dwDesiredAccess`中[MapViewOfFileEx](http://msdn.microsoft.com/library/windows/desktop/aa366763)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果輸入的參數無效，會發生判斷提示錯誤。  
  
##  <a name="operator_eq"></a>CAtlFileMappingBase::operator =  
 設定目前的檔案對應物件到另一個檔案對應物件。  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>參數  
 `orig`  
 目前的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 傳回目前物件的參考。  
  
##  <a name="unmap"></a>CAtlFileMappingBase::Unmap  
 呼叫這個方法來取消對應檔案對應物件。  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回`S_OK`上成功 」 或 「 錯誤`HRESULT`失敗。  
  
### <a name="remarks"></a>備註  
 請參閱[UnmapViewOfFile](http://msdn.microsoft.com/library/windows/desktop/aa366882)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlFileMapping 類別](../../atl/reference/catlfilemapping-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

