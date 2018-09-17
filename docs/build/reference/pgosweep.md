---
title: pgosweep |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed12828d9170aac576a97c63b9988bb4b303ef58
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711910"
---
# <a name="pgosweep"></a>pgosweep

用於特性指引最佳化，以從執行中的程式的所有設定檔資料寫入的.pgc 檔案。

## <a name="syntax"></a>語法

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>參數

*options*<br/>
（選擇性）有效值*選項*是：

- **/?** 或是 **/help**顯示說明訊息。

- **/noreset**會保留在執行階段資料結構中的計數。

*image*<br/>
使用所建立的.exe 或.dll 檔案的完整路徑[/GENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)， [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)，或[/ltcg: pginstrument](ltcg-link-time-code-generation.md)選項。

*pgcfile*<br/>
.Pgc 檔案，其中此命令會寫出資料計數。

## <a name="remarks"></a>備註

**Pgosweep**命令適用於使用所建置的程式[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)選項，或已被取代[/ltcg: pginstrument](ltcg-link-time-code-generation.md)選項。 它會中斷執行中的程式，並將設定檔資料寫入至新的.pgc 檔案。 根據預設，命令會重設計數之後每一個寫入作業。 如果您指定 **/noreset**選項時，命令將記錄的值，但不是在執行中的程式重設。 此選項可讓您重複的資料時，稍後擷取設定檔資料。

用於其他方面**pgosweep**是擷取設定檔資訊，只針對應用程式正常運作。 例如，您可以執行**pgosweep**短時間內啟動應用程式，並捨棄該檔案之後。 這會移除啟動成本與相關聯的設定檔資料。 然後，您可以執行**pgosweep**再結束應用程式。 現在所收集的資料會有使用者無法與程式互動的設定檔資訊只能從時間。

當您命名.pgc 檔 (使用*pgcfile*參數) 您可以使用標準格式，也就是*appname ！ n*.pgc。 如果您使用這種格式時，編譯器會自動尋找這些資料 **/LTCG /USEPROFILE**或是 **/ltcg: pgo 進行**階段。 如果您不使用標準格式，您必須使用[pgomgr](pgomgr.md)合併的.pgc 檔案。

> [!NOTE]
> 您可以啟動此工具只能從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

如需如何擷取設定檔內的資料從可執行檔的資訊，請參閱[PgoAutoSweep](pgoautosweep.md)。

## <a name="example"></a>範例

在此範例命令中， **pgosweep**寫入 myapp!1.pgc myapp.exe 的目前設定檔資訊。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
