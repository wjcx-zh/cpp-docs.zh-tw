---
title: 編譯器錯誤 C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344600"
---
# <a name="compiler-error-c3610"></a>編譯器錯誤 C3610

'valuetype': 實值型別必須 'boxed' 才能呼叫方法 'method'

根據預設，實值型別不是 managed 堆積上。 您可以從呼叫方法.NET 執行階段類別，例如之前`Object`，您需要將實值型別移至受控堆積。

C3610 才可使用過時的編譯器選項 **/clr: oldsyntax**。
