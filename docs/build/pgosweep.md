---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341189"
---
# <a name="pgosweep"></a>pgosweep

在特性指引優化中用來將執行中程式的所有設定檔資料寫入至 .pgc 檔案。

## <a name="syntax"></a>語法

> **pgosweep** [*選項*]*影像* *pgcfile*

### <a name="parameters"></a>參數

*options*<br/>
選擇性*選項*的有效值如下：

- **/?** 或 **/help**顯示說明訊息。

- **/noreset**會保留執行時間資料結構中的計數。

*image*<br/>
使用[/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)、 [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)或[/ltcg： PGINSTRUMENT](reference/ltcg-link-time-code-generation.md)選項所建立之 .exe 或 .dll 檔案的完整路徑。

*pgcfile*<br/>
.Pgc 檔，此命令會寫出資料計數。

## <a name="remarks"></a>備註

**Pgosweep**命令適用于使用[/GENPROFILE 或/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)選項所建立的程式，或已被取代的[/ltcg： PGINSTRUMENT](reference/ltcg-link-time-code-generation.md)選項。 它會中斷正在執行的程式，並將設定檔資料寫入新的 .pgc 檔案。 根據預設，命令會在每次寫入作業之後重設計數。 如果您指定 **/noreset**選項，此命令將會記錄這些值，但不會在執行中的程式中重設它們。 如果您稍後要取出分析資料，此選項會提供重複的資料。

**Pgosweep**的替代用法是只針對應用程式的正常作業來抓取設定檔資訊。 例如，您可以在啟動應用程式並捨棄該檔案之後，立即執行**pgosweep** 。 這會移除與啟動成本相關聯的設定檔資料。 然後，您可以在結束應用程式之前，先執行**pgosweep** 。 現在，收集的資料只有在使用者可以與程式互動的時間才會有設定檔資訊。

當您命名 .pgc 檔案時（藉由使用*pgcfile*參數），您可以使用標準格式，也就是*appname！ n*. .pgc。 如果您使用此格式，編譯器會自動在 **/LTCG/USEPROFILE**或 **/ltcg： PGO**階段中尋找這項資料。 如果您不使用標準格式，就必須使用[pgomgr](pgomgr.md)來合併 .pgc 檔案。

> [!NOTE]
> 您只能從 Visual Studio 的開發人員命令提示字元啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

如需有關如何從可執行檔中捕捉分析資料的詳細資訊，請參閱[PgoAutoSweep](pgoautosweep.md)。

## <a name="example"></a>範例

在此範例命令中， **pgosweep**會將 myapp .exe 的目前設定檔資訊寫入 myapp！ 1. .pgc。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>請參閱

[特性指引最佳化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
