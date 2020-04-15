---
title: FILE_TYPE_CODE枚舉
description: C++生成見解 SDK FILE_TYPE_CODE枚舉引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: dea603a072d7b2f472112a75b2e9ccded78399a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325568"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE枚舉

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`FILE_TYPE_CODE`舉描述檔的類型。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0 (0x000000) | 此枚舉中未列出的文件類型。 |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | 物件 (.obj)\*檔案。 |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2 (0x0000002) | 可執行檔\*(.exe)\*或 DLL (.dll) 檔案。 |
| `FILE_TYPE_CODE_LIB` | 3 (0x0000003) | 靜態庫 (*.lib) 檔案。 |
| `FILE_TYPE_CODE_IMP_LIB` | 4 (0x0000004) | 匯入函式庫 (lib) |
| `FILE_TYPE_CODE_EXP` | 5 (0x0000005) | 匯出 (*.exp) 檔案。 |

## <a name="remarks"></a>備註

::: moniker-end
