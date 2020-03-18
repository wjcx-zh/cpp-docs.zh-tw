---
title: LIB 輸入檔
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 209ba04ea43116b39f28b0790b7a1e2b3fb5ccd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439465"
---
# <a name="lib-input-files"></a>LIB 輸入檔

LIB 預期的輸入檔取決於使用它的模式，如下表所示。

|[模式]|輸入|
|----------|-----------|
|預設值（建立或修改程式庫）|COFF 物件（.obj）檔案，COFF 程式庫（.lib），32位物件模型格式（OMF）物件（.obj）檔案|
|使用/EXTRACT 解壓縮成員|COFF 程式庫（.lib）|
|使用/DEF 建立匯出檔案和匯入程式庫|模組定義（.def）檔案，COFF 物件（.obj）檔案，COFF 程式庫（.lib），32位 OMF 物件（.obj）檔案|

> [!NOTE]
>  由16位版本的 LIB 所建立的 OMF 程式庫，無法當做32位版本之 LIB 的輸入使用。

## <a name="see-also"></a>另請參閱

[LIB 概觀](overview-of-lib.md)
