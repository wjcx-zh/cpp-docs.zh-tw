---
title: 命令列錯誤 D8045
ms.date: 11/04/2016
f1_keywords:
- D8045
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
ms.openlocfilehash: 7964c2539b5358d2d946e530c4ee75110857446d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214192"
---
# <a name="command-line-error-d8045"></a>命令列錯誤 D8045

無法編譯 C 檔案 'file' 與 /clr 選項

只有C++原始程式碼檔可以傳遞至使用編譯 **/clr**。  使用 **/TP**到.c 檔案編譯為.cpp 檔案，請參閱[/Tc、 /Tp、 /TC、 /TP （指定原始程式檔類型）](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)如需詳細資訊。

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

如果您編譯 ATL 應用程式使用視覺效果，也會發生 D8045 C++。 請參閱[如何：移轉至 /clr](../../dotnet/how-to-migrate-to-clr.md)如需詳細資訊。