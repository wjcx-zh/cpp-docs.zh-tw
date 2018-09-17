---
title: LIB 輸出檔案 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23665897266bab87c71b8b3889688113fe8aa99a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720703"
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