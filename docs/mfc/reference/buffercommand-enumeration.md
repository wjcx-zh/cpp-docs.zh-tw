---
title: BufferCommand 列舉
description: 描述 BufferCommand 列舉，這是用來透過 CMemFile：： GetBufferPtr （）處理記憶體檔案
ms.date: 07/23/2020
f1_keywords:
- afx/buffercommand
helpviewer_keywords:
- buffercommand enumeration [MFC]
ms.openlocfilehash: f2f553df56fadd99b65b04cce9a97917425ed70b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246095"
---
# <a name="buffercommand-enumeration"></a>BufferCommand 列舉

由[CMemFile：： GetBufferPtr](cmemfile-class.md#getbufferptr)用來判斷要對檔案備份的記憶體緩衝區採取哪些動作。

## <a name="syntax"></a>語法

``` cpp
public enum BufferCommand
{
   bufferRead,
   bufferWrite,
   bufferCommit,
   bufferCheck
};
```

## <a name="members"></a>成員

|名稱|說明|
|-|-|
| `bufferRead` | 讀取檔案支援的記憶體緩衝區。 |
| `bufferWrite` | 寫入檔案支援的記憶體緩衝區。 |
| `bufferCommit` | 將檔案支援的記憶體緩衝區中目前的位置前移至認可緩衝區的結尾。 |
| `bufferCheck` | 判斷檔案備份的記憶體緩衝區大小是否可以成長。 |

## <a name="requirements"></a>需求

**標頭：** afxwinforms （定義于元件 atlmfc\lib\mfcmifc80.dll）
