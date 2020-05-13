---
title: LIB 輸入檔
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328221"
---
# <a name="lib-input-files"></a>LIB 輸入檔

LIB 預期的輸入檔取決於使用它的模式,如下表所示。

|[模式]|輸入|
|----------|-----------|
|預設值 (編譯或修改函式庫)|COFF 物件 (.obj) 檔案、COFF 函式庫 (.lib)、32 位物件模型格式 (OMF) 物件 (.obj) 檔案|
|使用 /EXTRACT 提取成員|COFF 函式庫 (.lib)|
|使用 /DEF 建譯匯出檔案及匯入庫|模組定義 (.def) 檔案、COFF 物件 (.obj) 檔案、COFF 函式庫 (.lib)、32 位元 OMF 物件 (.obj) 檔案|

> [!NOTE]
> 由 16 位元版本的 LIB 創建的 OMF 庫不能用作對 32 位版本的 LIB 的輸入。

## <a name="see-also"></a>另請參閱

[LIB 概觀](overview-of-lib.md)
