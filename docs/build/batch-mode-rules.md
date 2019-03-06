---
title: 批次模式規則
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 106db69327bbad112be7efea6970845956e52431
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416666"
---
# <a name="batch-mode-rules"></a>批次模式規則

```
{frompath}.fromext{topath}.toext::
   commands
```

當 N 命令進行此推斷規則時，批次模式推斷規則會提供推斷規則只有一個引動過程。 沒有批次模式推斷規則，它將需要 N 要叫用的命令。 N 是推斷規則觸發程序的相依項目數目。

包含批次模式推斷規則的 Makefile 必須使用 NMAKE 1.62 或更高版本。 若要檢查的 NMAKE 版本，1.62 或更新版本，NMAKE 版本搭配執行可用 _NMAKE_VER 巨集。 這個巨集會傳回字串，表示 Visual c + + 的產品版本。

之間唯一的語法差異的標準的推斷規則是以雙冒號 （:），終止批次模式推斷規則。

> [!NOTE]
>  叫用的工具必須能夠處理多個檔案。 必須使用批次模式推斷規則`$<`為巨集來存取相依檔案。

批次模式推斷規則可以加速建置程序。 這是更快提供給編譯器的批次中的檔案因為一次叫用編譯器的驅動程式。 例如，C 和 c + + 編譯器執行得更好處理一組檔案，因為它可以維持記憶體駐留在程序期間。

下列範例示範如何使用批次模式推斷規則：

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

NMAKE 會產生下列輸出，不含批次模式推斷規則：

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

NMAKE 會產生下列結果與批次模式推斷規則：

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

[推斷規則](../build/inference-rules.md)
