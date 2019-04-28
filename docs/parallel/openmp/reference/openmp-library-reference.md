---
title: OpenMP 程式庫參考
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362513"
---
# <a name="openmp-library-reference"></a>OpenMP 程式庫參考

提供建構 OpenMP API 中使用的連結。

視覺效果C++實作的 OpenMP 標準包含下列建構函式。

|建構|描述|
|---------------|-----------------|
|[指示詞](openmp-directives.md)|提供用於 OpenMP API 中的指示詞的連結。|
|[子句](openmp-directives.md)|提供給子句在 OpenMP API 中使用的連結。|
|[函式](openmp-functions.md)|提供在 OpenMP API 中使用的函式連結。|
|[環境變數](openmp-environment-variables.md)|提供連結 OpenMP API 中使用的環境變數。|

視覺效果C++OpenMP 執行階段程式庫函式都包含下列的程式庫中。

|OpenMP 執行階段程式庫|特性|
|------------------------------|---------------------|
|VCOMP.LIB|多執行緒、 動態連結 （如 VCOMP 匯入程式庫。LIB)。|
|VCOMPD.LIB|多執行緒、 動態連結 （如 VCOMPD 匯入程式庫。筆記電腦螢幕） （偵錯）|

如果在編譯中定義 _DEBUG，而且如果`#include omp.h`原始程式碼，VCOMPD 中。LIB 會預設程式庫，否則 VCOMP。將會使用 LIB。

您可以使用[/NODEFAULTLIB （忽略程式庫）](../../../build/reference/nodefaultlib-ignore-libraries.md)移除預設程式庫，並明確地連結您所選擇的程式庫。

OpenMP Dll 會在視覺效果C++可轉散發套件的目錄以及使用 OpenMP 應用程式一起散發的需求。

## <a name="see-also"></a>另請參閱

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)