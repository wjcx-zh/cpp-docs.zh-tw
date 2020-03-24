---
title: 編譯器 COM 全域函式
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: c0a9c742ad9dcbb05ed2d78c954d5a597e3b57cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189776"
---
# <a name="compiler-com-global-functions"></a>編譯器 COM 全域函式

**Microsoft 專屬**

下列為可用的處理常式：

|函式|描述|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|會擲回[_com_error](../cpp/com-error-class.md)以回應失敗。|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|取代 COM 錯誤處理所使用的預設函式。|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|將 `BSTR` 值轉換成 `char *`。|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|將 `char *` 值轉換成 `BSTR`。|

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[編譯器 COM 支援](../cpp/compiler-com-support.md)
