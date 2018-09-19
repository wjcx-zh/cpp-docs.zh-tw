---
title: CSimpleDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f58efa7b7ba5c0452f2418a2dbbc27c94eedaca6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087951"
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

*t_bCenter*<br/>
如果對話方塊物件擁有者 視窗中，位於中央，則為 TRUE。否則為 FALSE。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|建立強制回應對話方塊。|

## <a name="remarks"></a>備註

實作基本功能的強制回應對話方塊。 `CSimpleDialog` 提供 Windows 通用控制項僅支援。 若要建立並顯示強制回應對話方塊中，建立這個對話方塊中提供現有的資源範本的名稱的類別的執行個體。 當使用者按下任何控制項 （例如 IDOK 或 IDCANCEL） 的預先定義的值時，就會關閉對話方塊物件。

`CSimpleDialog` 可讓您建立只能強制回應對話方塊。 `CSimpleDialog` 提供的對話方塊方塊程序，會使用預設的訊息對應將導向至適當的處理常式的訊息。

請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)如需詳細資訊。

## <a name="inheritance-hierarchy"></a>繼承階層

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="domodal"></a>  CSimpleDialog::DoModal

叫用強制回應對話方塊，並傳回完成的對話方塊結果。

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>參數

*hWndParent*<br/>
對話方塊的父控制代碼。 如果未不提供任何值，父代設為目前使用中視窗。

### <a name="return-value"></a>傳回值

如果成功，傳回的值會是關閉的對話方塊控制項的資源識別碼。

如果函式失敗，傳回的值為-1。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

對話方塊為作用中時，這個方法會處理使用者的所有互動。 這是讓對話方塊強制回應;也就是使用者無法互動與其他視窗中，直到在關閉對話方塊。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
