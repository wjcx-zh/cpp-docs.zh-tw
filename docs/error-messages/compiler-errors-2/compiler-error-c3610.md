---
title: 編譯器錯誤 C3610 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037849"
---
# <a name="compiler-error-c3610"></a>編譯器錯誤 C3610

'valuetype': 實值型別必須 'boxed' 才能呼叫方法 'method'

根據預設，實值型別不是 managed 堆積上。 您可以從呼叫方法.NET 執行階段類別，例如之前`Object`，您需要將實值型別移至受控堆積。

C3610 才可使用過時的編譯器選項 **/clr: oldsyntax**。
