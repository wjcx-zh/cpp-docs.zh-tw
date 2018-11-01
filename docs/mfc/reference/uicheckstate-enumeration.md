---
title: UICheckState 列舉
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 6e04015f33012ddd1c0a75187c89eadedbe01e3d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528137"
---
# <a name="uicheckstate-enumeration"></a>UICheckState 列舉
描述命令的使用者介面項目核取狀態。

### <a name="syntax"></a>語法

```
public enum class
{
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]
   Unchecked,
   Checked,
   Indeterminate
};
```

### <a name="remarks"></a>備註

[ICommandUI::Check](icommandui-interface.md#check)會使用這些值來描述使用者介面項目的狀態。
如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

### <a name="requirements"></a>需求

**標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）
