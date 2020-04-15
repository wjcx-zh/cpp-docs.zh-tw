---
title: 批次模式規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328403"
---
# <a name="batch-mode-rules"></a>批次模式規則

```
{frompath}.fromext{topath}.toext::
   commands
```

當 N 命令通過此推理規則時,批處理模式推理規則僅提供一個推理規則的調用。 如果沒有批處理模式推理規則,則需要調用 N 命令。 N 是觸發推理規則的從屬項數。

製作包含批次處理模式推理規則的檔必須使用 NMAKE 版本 1.62 或更高版本。 要檢查 NMAKE 版本,請運行與 NMAKE 版本 1.62 或更高版本的_NMAKE_VER宏。 此宏返回表示 VisualC++產品版本的字串。

與標準推理規則的唯一語法區別是批處理模式推理規則終止了雙冒號 (::)。

> [!NOTE]
> 正在呼叫的工具必須能夠處理多個檔。 批次處理模式推理規則必須用作`$<`宏才能存取相關文件。

批次處理模式推理規則可以加快生成過程。 批量向編譯器提供檔會更快,因為編譯器驅動程式只調用一次。 例如,在處理一組檔時,C 和C++編譯器性能更好,因為它可以在過程中保持記憶體駐留。

下面的範例展示如何使用批次處理模式推理規則:

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE 產生以下輸出,無需批次處理模式推理規則:

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE 使用批次處理模式推理規則產生以下結果:

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>另請參閱

[推斷規則](inference-rules.md)
