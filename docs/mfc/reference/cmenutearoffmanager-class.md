---
title: "CMenuTearOffManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
dev_langs:
- C++
helpviewer_keywords:
- CMenuTearOffManager class
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: 31
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
ms.openlocfilehash: 53677bbea54e428e5f080f5c1f73c576abcf99a5
ms.lasthandoff: 02/24/2017

---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 類別
管理 Tear-Off 功能表。 Tear-Off 功能表是在功能表列上的功能表。 使用者可以取下功能表列中的 Tear-Off 功能表，讓 Tear-Off 功能表浮動。  
  
## <a name="syntax"></a>語法  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|建構 `CMenuTearOffManager` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|初始化`CMenuTearOffManager`物件。|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>備註  
 若要使用應用程式中的 tear-off 功能表，您必須擁有`CMenuTearOffManager`物件。 在大部分情況下，您將不會建立或初始化`CMenuTearOffManager`直接物件。 這會為您處理當您呼叫[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)函式。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構和初始化`CMenuTearOffManager`物件呼叫`CWinAppEX::EnableTearOffMenus`方法。 此程式碼片段是一部分[字板範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&12;](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmenutearoffmanager.h  
  
##  <a name="build"></a>CMenuTearOffManager::Build  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiTearOffBarID`  
 [in] `strText`  
  
### <a name="remarks"></a>備註  
  
##  <a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager  
 建構[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不應該建立`CMenuTearOffManager`手動。 您的應用程式的架構建立`CMenuTearOffManager`物件當您呼叫[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)。  
  
##  <a name="getregpath"></a>CMenuTearOffManager::GetRegPath  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="initialize"></a>CMenuTearOffManager::Initialize  
 初始化[CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)物件。  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszRegEntry`  
 字串，其中包含登錄項目路徑。 您的應用程式儲存撕條的設定，此登錄項目中。  
  
 [in] `uiTearOffMenuFirst`  
 Tear-off 功能表將第一個功能表識別碼。  
  
 [in] `uiTearOffMenuLast`  
 Tear-off 功能表最後一個功能表識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 從功能表識別碼的範圍`uiTearOffMenuFirst`至`uiTearOffMenuLast`必須是連續的間隔。 此間隔定義 tear-off 功能表可在應用程式中同時顯示的數目。  
  
##  <a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiID`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="parse"></a>CMenuTearOffManager::Parse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>參數  
 [in] `str`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="reset"></a>CMenuTearOffManager::Reset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hmenu`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setinuse"></a>CMenuTearOffManager::SetInUse  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmdId`  
 [in] `bUse`  
  
### <a name="remarks"></a>備註  
  
##  <a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>參數  
 [in] `hMenu`  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [Cwinappex 衍生類別](../../mfc/reference/cwinappex-class.md)

