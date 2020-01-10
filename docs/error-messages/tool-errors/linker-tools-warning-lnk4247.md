---
title: 連結器工具警告 LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991149"
---
# <a name="linker-tools-warning-lnk4247"></a>連結器工具警告 LNK4247

進入點 ' decorated_function_name ' 已經有 thread 屬性;已忽略 ' attribute '

以[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)指定的進入點具有線程屬性，但也指定了[/CLRTHREADATTRIBUTE （設定 CLR 執行緒屬性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) ，並使用不同的執行緒模型。

連結器已忽略以/CLRTHREADATTRIBUTE. 指定的值

若要解決此警告：

- 從您的組建中移除/CLRTHREADATTRIBUTE。

- 從原始程式碼檔中移除屬性。

- 從您的組建中移除來源和/CLRTHREADATTRIBUTE 的屬性，並接受預設的 CLR 執行緒模型。

- 變更傳遞給/CLRTHREADATTRIBUTE 的值，如此一來，它就會同意來源中的屬性。

- 變更來源中的屬性，如此一來，它會同意傳遞給/CLRTHREADATTRIBUTE. 的值。

下列範例會產生 LNK4247

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
