---
title: UICheckState 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxwinforms/uicheckstate
dev_langs:
- C++
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11c326de6b30668265ff57de73021bcd526baa5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
   
### <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  
