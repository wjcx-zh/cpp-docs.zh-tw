---
title: CAtlFileMappingBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f07f14cca7ea0346cc6772d3dca959af07a05cd
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218158"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 類別
此類別代表的記憶體對應檔。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CAtlFileMappingBase
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|建構函式。|  
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|呼叫這個方法來複製檔案對應物件。|  
|[CAtlFileMappingBase::GetData](#getdata)|呼叫這個方法來取得檔案對應物件中的資料。|  
|[CAtlFileMappingBase::GetHandle](#gethandle)|呼叫這個方法傳回的檔案控制代碼。|  
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|呼叫這個方法來取得對應大小的檔案對應物件。|  
|[CAtlFileMappingBase::MapFile](#mapfile)|呼叫這個方法來建立檔案對應物件。|  
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|呼叫這個方法來建立檔案對應物件，以允許所有處理程序的完整存取。|  
|[CAtlFileMappingBase::OpenMapping](#openmapping)|呼叫這個方法來傳回檔案對應物件的控制代碼。|  
|[CAtlFileMappingBase::Unmap](#unmap)|呼叫這個方法來取消對應檔案對應物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CAtlFileMappingBase::operator =](#operator_eq)|設定目前的檔案對應物件到另一個檔案對應物件。|  
  
## <a name="remarks"></a>備註  
 檔案對應是與之間的關聯檔案的內容的處理程序虛擬位址空間的一部分。 這個類別提供方法來建立允許程式輕鬆地存取及共用資料的檔案對應物件。  
  
 如需詳細資訊，請參閱 <<c0> [ 檔案對應](/windows/desktop/Memory/file-mapping)Windows SDK 中。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlfile.h  
  
##  <a name="catlfilemappingbase"></a>  CAtlFileMappingBase::CAtlFileMappingBase  
 建構函式。  
  
```
CAtlFileMappingBase(CAtlFileMappingBase& orig);  
CAtlFileMappingBase() throw();
```  
  
### <a name="parameters"></a>參數  
 *orig*  
 若要建立新的物件複製原始的檔案對應物件。  
  
### <a name="remarks"></a>備註  
 建立新的檔案對應物件，選擇性地使用現有的物件。 仍然必須呼叫[CAtlFileMappingBase::MapFile](#mapfile)開啟或建立特定的檔案所需的檔案對應物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]  
  
##  <a name="dtor"></a>  CAtlFileMappingBase:: ~ CAtlFileMappingBase  
 解構函式。  
  
```
~CAtlFileMappingBase() throw();
```  
  
### <a name="remarks"></a>備註  
 會釋放所有資源配置的類別並呼叫[CAtlFileMappingBase::Unmap](#unmap)方法。  
  
##  <a name="copyfrom"></a>  CAtlFileMappingBase::CopyFrom  
 呼叫這個方法來複製檔案對應物件。  
  
```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```  
  
### <a name="parameters"></a>參數  
 *orig*  
 若要從複製原始的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
##  <a name="getdata"></a>  CAtlFileMappingBase::GetData  
 呼叫這個方法來取得檔案對應物件中的資料。  
  
```
void* GetData() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回資料的指標。  
  
##  <a name="gethandle"></a>  CAtlFileMappingBase::GetHandle  
 呼叫這個方法來傳回檔案對應物件的控制代碼。  
  
```
HANDLE GetHandle() throw ();
```  
  
### <a name="return-value"></a>傳回值  
 傳回檔案對應物件的控制代碼。  
  
##  <a name="getmappingsize"></a>  CAtlFileMappingBase::GetMappingSize  
 呼叫這個方法來取得對應大小的檔案對應物件。  
  
```
SIZE_T GetMappingSize() throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回對應的大小。  
  
### <a name="example"></a>範例  
 範例，請參閱[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapfile"></a>  CAtlFileMappingBase::MapFile  
 呼叫這個方法來開啟或建立的指定檔案的檔案對應物件。  
  
```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```  
  
### <a name="parameters"></a>參數  
 *hFile*  
 要從中建立對應物件的檔案控制代碼。 *hFile*必須有效，而且不能設為 INVALID_HANDLE_VALUE。  
  
 *nMappingSize*  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別之檔案的目前大小*hFile。*  
  
 *nOffset*  
 對應到開始的所在檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 *dwMappingProtection*  
 在對應檔案時，檔案檢視所需的保護。 請參閱*flProtect*中[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK 中。  
  
 *dwViewDesiredAccess*  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 已建立的檔案對應物件之後，檔案大小不得超過檔案對應物件的大小若是如此，不是所有檔案的內容可供共用。 如需詳細資訊，請參閱 < [CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)並[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="example"></a>範例  
 範例，請參閱[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)。  
  
##  <a name="mapsharedmem"></a>  CAtlFileMappingBase::MapSharedMem  
 呼叫這個方法來建立檔案對應物件，以允許所有處理程序的完整存取。  
  
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
 *nMappingSize*  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小*szName*。  
  
 *szName*  
 對應物件的名稱。  
  
 *pbAlreadyExisted*  
 指向 BOOL 值，設為 TRUE 的對應物件已經存在。  
  
 *lpsa*  
 將指標`SECURITY_ATTRIBUTES`判斷子處理序是否可以繼承傳回的控制代碼的結構。 請參閱*lpAttributes*中[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga) Windows SDK 中。  
  
 *dwMappingProtection*  
 在對應檔案時，針對 [檔案] 檢視中，所需的保護。 請參閱*flProtect*在`CreateFileMapping`Windows SDK 中。  
  
 *dwViewDesiredAccess*  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 `MapShareMem` 可讓現有的檔案對應物件，由[CreateFileMapping](/windows/desktop/api/winbase/nf-winbase-createfilemappinga)、 處理序之間共用。  
  
##  <a name="openmapping"></a>  CAtlFileMappingBase::OpenMapping  
 呼叫這個方法，以開啟已命名的檔案對應物件，指定的檔案。  
  
```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```  
  
### <a name="parameters"></a>參數  
 *szName*  
 對應物件的名稱。 如果沒有這個名稱的檔案對應物件的開啟控制代碼，而且沒有與衝突上的對應物件的安全性描述元*dwViewDesiredAccess*參數，開啟作業成功。  
  
 *nMappingSize*  
 對應的大小。 如果為 0，檔案對應物件的大小上限等於所識別的檔案對應物件的目前大小*szName*。  
  
 *nOffset*  
 對應到開始的所在檔案位移。 位移的值必須是系統的記憶體配置資料粒度的倍數。  
  
 *dwViewDesiredAccess*  
 指定檔案檢視，因此，對應的分頁檔所保護的存取的類型。 請參閱*dwDesiredAccess*中[MapViewOfFileEx](https://msdn.microsoft.com/library/windows/desktop/aa366763) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 在偵錯組建中，如果輸入的參數無效，會發生判斷提示錯誤。  
  
##  <a name="operator_eq"></a>  CAtlFileMappingBase::operator =  
 設定目前的檔案對應物件到另一個檔案對應物件。  
  
```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```  
  
### <a name="parameters"></a>參數  
 *orig*  
 目前的檔案對應物件。  
  
### <a name="return-value"></a>傳回值  
 傳回目前物件的參考。  
  
##  <a name="unmap"></a>  CAtlFileMappingBase::Unmap  
 呼叫這個方法來取消對應檔案對應物件。  
  
```
HRESULT Unmap() throw();
```  
  
### <a name="return-value"></a>傳回值  
 會傳回 S_OK，如果成功或失敗的錯誤 HRESULT。  
  
### <a name="remarks"></a>備註  
 請參閱[UnmapViewOfFile](https://msdn.microsoft.com/library/windows/desktop/aa366882)在 Windows SDK 中，如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlFileMapping 類別](../../atl/reference/catlfilemapping-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
