---
title: LIB 輸出檔案
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: bc505a9a946f564425513dad8107fd962eb054b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562889"
---
# <a name="lib-output-files"></a>LIB 輸出檔案

下表所示，程式庫所產生的輸出檔會取決於所在正，模式。

|模式|輸出|
|----------|------------|
|預設值 （建立或修改程式庫）|COFF 程式庫 (.lib)|
|擷取的成員具有 /EXTRACT|目的檔 (.obj)|
|建立匯出檔案，並匯入 /DEF 程式庫|匯入程式庫 (.lib) 和匯出 (.exp) 檔案|

## <a name="see-also"></a>另請參閱

[LIB 概觀](../../build/reference/overview-of-lib.md)