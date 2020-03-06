---
title: FILE_TYPE_CODE 列舉
description: C++ BUILD Insights SDK FILE_TYPE_CODE 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_TYPE_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e64f9315c62ce40c436032d6c96fdfa725847a7f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333717"
---
# <a name="file_type_code-enum"></a>FILE_TYPE_CODE 列舉

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_TYPE_CODE` 列舉會描述檔案的類型。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `FILE_TYPE_CODE_OTHER` | 0（0x00000000） | 未列在此列舉中的檔案類型。 |
| `FILE_TYPE_CODE_OBJ` | 1 (0x00000001) | 物件（\*.obj）檔案。 |
| `FILE_TYPE_CODE_EXECUTABLE_IMAGE` | 2（0x00000002） | 可執行檔（\*.exe）或 DLL （\*.dll）檔案。 |
| `FILE_TYPE_CODE_LIB` | 3（0x00000003） | 靜態程式庫（* .lib）檔案。 |
| `FILE_TYPE_CODE_IMP_LIB` | 4（0x00000004） | 匯入程式庫（* .lib） |
| `FILE_TYPE_CODE_EXP` | 5（0x00000005） | 匯出（* .exp）檔案。 |

## <a name="remarks"></a>備註

::: moniker-end
