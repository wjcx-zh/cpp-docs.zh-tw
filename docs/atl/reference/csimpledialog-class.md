---
title: C簡單對話類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330823"
---
# <a name="csimpledialog-class"></a>C簡單對話類別

此類實現基本模式對話方塊。

## <a name="syntax"></a>語法

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>參數

*t_wDlgTemplateID*

對話框範本資源的資源 ID。

*t_bCenter*<br/>
如果對話框物件要居於所有者視窗,則為 TRUE;如果對話框物件要位於擁有者視窗上,則為 TRUE。否則 FALSE。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C簡單對話::Do模態](#domodal)|創建模式對話方塊。|

## <a name="remarks"></a>備註

實現具有基本功能的模式對話方塊。 `CSimpleDialog`僅支援 Windows 公共控件。 要創建和顯示模態對話框,請創建此類的實例,為對話方塊提供現有資源範本的名稱。 當用戶單擊具有預定義值(如 IDOK 或 IDCANCEL)的任何控制項時,對話方塊物件將關閉。

`CSimpleDialog`允許您僅建立模式對話方塊。 `CSimpleDialog`提供對話框過程,該過程使用預設消息映射將消息定向到相應的處理程式。

有關詳細資訊[,請參閱實現對話框](../../atl/implementing-a-dialog-box.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>C簡單對話::Do模態

調用模態對話框,並在完成後返回對話框結果。

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>參數

*hWnd 父母*<br/>
對話框父級的句柄。 如果未提供任何值,則父級設置為當前活動視窗。

### <a name="return-value"></a>傳回值

如果成功,返回值是取消對話框的控制項的資源 ID。

如果函數失敗,返回值為 -1。 若要取得延伸錯誤資訊，請呼叫 `GetLastError`。

### <a name="remarks"></a>備註

此方法處理與使用者的所有交互,當對話框處於活動狀態時。 這就是使對話框模態的原因;也就是說,在關閉對話方塊之前,用戶無法與其他窗互。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
