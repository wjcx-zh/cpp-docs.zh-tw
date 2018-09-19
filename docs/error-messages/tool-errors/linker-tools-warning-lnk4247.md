---
title: 連結器工具警告 LNK4247 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078006"
---
# <a name="linker-tools-warning-lnk4247"></a>連結器工具警告 LNK4247

進入點 'decorated_function_name' 已經有一個執行緒屬性;忽略 ' attribute'

進入點，以指定[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)，有一個執行緒的屬性，但[/CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)也指定了，使用不同的執行緒模型。

連結器會忽略 /CLRTHREADATTRIBUTE 與指定的值。

若要解決這個警告：

- /CLRTHREADATTRIBUTE 移除您的組建。

- 從您的原始程式碼檔中移除屬性。

- 從來源和 /CLRTHREADATTRIBUTE 移除這兩個屬性，從您的組建，並接受預設 CLR 執行緒模型。

- 變更的值傳遞至 /CLRTHREADATTRIBUTE，使得它接納來源內的屬性。

- 變更來源中的屬性，使它同意 /CLRTHREADATTRIBUTE 來傳遞的值。

下列範例會產生 LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```