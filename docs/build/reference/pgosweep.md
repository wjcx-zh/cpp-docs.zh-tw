---
title: pgosweep |Microsoft 文件
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
ms.openlocfilehash: ded5b692d7c51e5a46a325a69ad6969083025ff5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="pgosweep"></a>pgosweep

將所有設定檔資料執行中程式寫入.pgc 檔用於特性指引最佳化。

## <a name="syntax"></a>語法

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>參數

*選項*（選擇性）<br/>
有效值*選項*是：

- **/?** 或 **/help**顯示說明訊息。

- **/noreset**保留的執行階段資料結構中的計數。

*image*<br/>
使用所建立的.exe 或.dll 檔案的完整路徑[/GENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)， [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)，或[/ltcg: pginstrument](ltcg-link-time-code-generation.md)選項。

*pgcfile*<br/>
此命令寫入位置出的資料計數.pgc 檔案。

## <a name="remarks"></a>備註

**Pgosweep**命令的運作方式程式所建立的使用[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)選項，或已被取代[/ltcg: pginstrument](ltcg-link-time-code-generation.md)選項。 它會中斷正在執行的程式，並將設定檔資料寫入至新的.pgc 檔案。 根據預設，命令會重設次數之後每一個寫入作業。 如果您指定 **/noreset**選項時，命令將記錄的值，但不是會重設執行中的程式中。 此選項可讓您重複的資料如果您稍後擷取分析資料。

用於其他方面**pgosweep**是擷取只針對應用程式的正常運作的設定檔資訊。 例如，您可以執行**pgosweep**短時間內啟動應用程式，並捨棄該檔案之後。 這會移除與啟動成本相關聯的設定檔資料。 然後，您可以執行**pgosweep**再結束應用程式。 現在所收集的資料具有使用者可與程式互動的設定檔資訊只會從時間。

.Pgc 檔案的名稱時 (使用*pgcfile*參數) 您可以使用標準格式，這是*appname ！ n*.pgc。 如果您使用此格式時，編譯器會自動尋找此資料在 **/LTCG /USEPROFILE**或 **/ltcg: pgo 進行**階段。 如果您不使用標準格式，您必須使用[pgomgr](pgomgr.md)合併的.pgc 檔案。

> [!NOTE]
> 您可以啟動這個工具只會從 Visual Studio 開發人員命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

如需如何擷取在您可執行檔的設定檔資料的資訊，請參閱[PgoAutoSweep](pgoautosweep.md)。

## <a name="example"></a>範例

在此範例命令中， **pgosweep**寫入 myapp!1.pgc myapp.exe 的目前設定檔資訊。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>另請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
