---
title: OpenMP 程式庫參考
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810746"
---
# <a name="openmp-library-reference"></a>OpenMP 程式庫參考

提供 OpenMP API 中使用的結構連結。

OpenMP 標準C++的視覺化執行包括下列結構。

|建構|描述|
|---------------|-----------------|
|[指示詞](openmp-directives.md)|提供 OpenMP API 中使用的指示詞連結。|
|[子句](openmp-clauses.md)|提供 OpenMP API 中使用之子句的連結。|
|[函式](openmp-functions.md)|提供 OpenMP API 中使用之函式的連結。|
|[環境變數](openmp-environment-variables.md)|提供 OpenMP API 中使用之環境變數的連結。|

Visual C++ OpenMP 執行時間程式庫函式包含在下列程式庫中。

|OpenMP 執行時間程式庫|特性|
|------------------------------|---------------------|
|VCOMP.LIB|多執行緒，動態連結（VCOMP140 的匯入程式庫。DLL）。|
|VCOMPD.LIB|多執行緒，動態連結（VCOMP140D 的匯入程式庫。DLL）（debug）|

如果 _DEBUG 是在編譯中定義，而且如果 `#include <omp.h>` 是在原始程式碼中，則 VCOMPD。LIB 會是預設的 lib，否則會是 VCOMP。將會使用 LIB。

您可以使用[/NODEFAULTLIB （忽略程式庫）](../../../build/reference/nodefaultlib-ignore-libraries.md)來移除預設 lib，並明確地連結至您選擇的 lib。

OpenMP Dll 位於 Visual C++可轉散發目錄中，而且必須與使用 OpenMP 的應用程式一起散發。

## <a name="see-also"></a>請參閱

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
