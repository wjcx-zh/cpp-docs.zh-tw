---
title: Visual Studio 2015 和 Visual Studio 2017 之間的 C++ 二進位相容性 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cedef2d5343b93c544ab22c41d2e5ac661bc3dd
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169563"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 和 Visual Studio 2017 之間的 C++ 二進位相容性

在舊版的 Visual Studio 中，使用不同版本的編譯器工具組和執行階段程式庫在目的檔 (OBJ)、靜態程式庫 (LIB)、動態程式庫 (DLL) 和可執行檔 (EXE) 之間所建立的二進位相容性不受保證。 這在 Visual Studio 2017 中已變更。 在 Visual Studio 2015 和 Visual Studio 2017 中，C++ 工具組的主要版本號碼為 14 (Visual Studio 2015 為 v140，Visual Studio 2017 為 v141)。 這反映以任一編譯器版本編譯的執行階段程式庫和應用程式大部分為二進位相容的。 這表示，例如若您在 Visual Studio 2015 中有 DLL，不需要重新編譯它，就可以從使用 Visual Studio 2017 建置的應用程式取用它。  

這項規則有兩個例外。 在下列情況下，不保證二進位相容性：  

1. 使用 `/GL` 編譯器參數編譯靜態程式庫或目的檔時。  

2. 當取用程式庫時，其建置所用的工具組版本高於用於編譯及連結應用程式之工具組時。 例如，以編譯器版本 19.12 編譯及連結的程式可取用以編譯器 19.0 至 19.12 編譯的程式庫。 此外，二進位相容性只存在於 Visual Studio 2015 和 Visual Studio 2017 之間，不支援連結 19.x 程式與 Visual Studio 2013 或更舊版本所產生的程式庫。

## <a name="see-also"></a>請參閱  

[Visual C++ 變更歷程記錄](..\porting\visual-cpp-change-history-2003-2015.md)
