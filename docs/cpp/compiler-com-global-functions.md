---
title: 編譯器 COM 全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb769cf1419f7a0142a5eeae348ca432f78fb92a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034133"
---
# <a name="compiler-com-global-functions"></a>編譯器 COM 全域函式

**Microsoft 專屬**

下列為可用的處理常式：

|功能|描述|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|會擲回[_com_error](../cpp/com-error-class.md)以回應失敗。|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|取代 COM 錯誤處理所使用的預設函式。|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|將轉換`BSTR`值`char *`。|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|將轉換`char *`值`BSTR`。|

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[編譯器 COM 支援](../cpp/compiler-com-support.md)