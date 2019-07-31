---
title: OpenMP 程式庫參考
ms.date: 07/30/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: c78c2677741714ab48d49a4443ad753369ec4500
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682585"
---
# <a name="openmp-library-reference"></a>OpenMP 程式庫參考

提供 OpenMP API 中使用的結構連結。

OpenMP 標準C++的視覺化執行包括下列結構。

|建構|說明|
|---------------|-----------------|
|[指示詞](openmp-directives.md)|提供 OpenMP API 中使用的指示詞連結。|
|[子句](openmp-clauses.md)|提供 OpenMP API 中使用之子句的連結。|
|[函式](openmp-functions.md)|提供 OpenMP API 中使用之函式的連結。|
|[環境變數](openmp-environment-variables.md)|提供 OpenMP API 中使用之環境變數的連結。|

Visual C++ OpenMP 執行時間程式庫函式包含在下列程式庫中。

|OpenMP 執行時間程式庫|特性|
|------------------------------|---------------------|
|VCOMP.LIB|多執行緒, 動態連結 (VCOMP 的匯入程式庫。LIB)。|
|VCOMPD.LIB|多執行緒, 動態連結 (VCOMPD 的匯入程式庫。蓋) (debug)|

如果 _debug 是在編譯中定義, 而且`#include omp.h`如果是在原始程式碼中, 則 VCOMPD。LIB 會是預設的 lib, 否則會是 VCOMP。將會使用 LIB。

您可以使用[/NODEFAULTLIB (忽略程式庫)](../../../build/reference/nodefaultlib-ignore-libraries.md)來移除預設 lib, 並明確地連結至您選擇的 lib。

OpenMP Dll 位於 Visual C++可轉散發目錄中, 而且必須與使用 OpenMP 的應用程式一起散發。

## <a name="see-also"></a>另請參閱

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)