---
title: LIB 輸出檔案
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: 31c69a273d9f201046171ecc8889dda6e07328d6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419318"
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
