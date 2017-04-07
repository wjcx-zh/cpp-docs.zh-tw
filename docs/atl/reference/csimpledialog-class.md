---
title: "CSimpleDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
caps.latest.revision: 19
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
ms.openlocfilehash: a4c17a1da8d1be00ebff171af09bc6c8eb81ed44
ms.lasthandoff: 02/24/2017

---
# <a name="csimpledialog-class"></a>CSimpleDialog 類別
這個類別會實作基本的強制回應對話方塊。  
  
## <a name="syntax"></a>語法  
  
```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>  
class CSimpleDialog : public CDialogImplBase
```  
  
#### <a name="parameters"></a>參數  
 *t_wDlgTemplateID*  
  
 對話方塊範本資源的資源識別碼。  
  
 *t_bCenter*  
 **TRUE**對話方塊物件為擁有者視窗上置中; 否則**FALSE**。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSimpleDialog::DoModal](#domodal)|建立強制回應對話方塊。|  
  
## <a name="remarks"></a>備註  
 會強制回應對話方塊實作的基本功能。 `CSimpleDialog`提供 Windows 通用控制項僅支援。 若要建立並顯示強制回應對話方塊，建立這個類別，提供現有的資源範本名稱 對話方塊中的執行個體。 當使用者按下任何控制項的預先定義的值 （例如 IDOK 或 IDCANCEL） 時，就會關閉對話方塊物件。  
  
 `CSimpleDialog`可讓您建立只有強制回應對話方塊。 `CSimpleDialog`提供將訊息導向到適當的處理常式會使用預設的訊息對應的對話方塊方塊程序。  
  
 請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)如需詳細資訊。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDialogImplBase`  
  
 `CSimpleDialog`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlwin.h  
  
##  <a name="domodal"></a>CSimpleDialog::DoModal  
 叫用強制回應對話方塊，並傳回完成的對話方塊結果。  
  
```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```  
  
### <a name="parameters"></a>參數  
 `hWndParent`  
 父系 對話方塊中的控制代碼。 如果未不提供任何值，父代設為目前使用中視窗。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則傳回的值會是關閉的對話方塊控制項的資源識別碼。  
  
 如果函式失敗，傳回值為 –&1;。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。  
  
### <a name="remarks"></a>備註  
 對話方塊中正在作用中時，此方法會處理所有的使用者互動。 這是讓對話方塊強制回應。也就是使用者無法互動與其他視窗中，直到關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

