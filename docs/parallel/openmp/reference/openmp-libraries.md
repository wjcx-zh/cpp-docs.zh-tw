---
title: OpenMP 程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7620b0ea710a5474fbbbf614691ceeb1e5cc945e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061998"
---
# <a name="openmp-libraries"></a>OpenMP 程式庫

討論組成 Visual c + + OpenMP 執行階段程式庫的.lib 檔案。

下列程式庫包含 Visual c + + OpenMP 執行階段程式庫函式。

|OpenMP 執行階段程式庫|特性|
|------------------------------|---------------------|
|VCOMP.LIB|多執行緒、 動態連結 （如 VCOMP 匯入程式庫。LIB)。|
|VCOMPD.LIB|多執行緒、 動態連結 （如 VCOMPD 匯入程式庫。筆記電腦螢幕） （偵錯）|

如果在編譯中定義 _DEBUG，而且如果`#include omp.h`原始程式碼，VCOMPD 中。LIB 會預設程式庫。 否則，VCOMP。將會使用 LIB。

您可以使用[/NODEFAULTLIB （忽略程式庫）](../../../build/reference/nodefaultlib-ignore-libraries.md)移除預設程式庫，並明確地連結您所選擇的程式庫。

OpenMP Dll 會在 Visual c + + 可轉散發套件目錄中，而且需要使用 OpenMP 應用程式一起散發。

## <a name="see-also"></a>另請參閱

[程式庫參考](openmp-library-reference.md)
