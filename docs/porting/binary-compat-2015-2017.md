---
title: "Visual Studio 2015 和 Visual Studio 2017 之間的 C++ 二進位相容性 | Microsoft Docs"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d527a4e0647fe0e8471e168841a93512f4d1a9e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2017"></a>Visual Studio 2015 和 Visual Studio 2017 之間的 C++ 二進位相容性


在舊版的 Visual Studio 中，使用不同版本的編譯器工具組和執行階段程式庫在目的檔 (OBJ)、靜態程式庫 (LIB)、動態程式庫 (DLL) 和可執行檔 (EXE) 之間所建立的二進位相容性不受保證。 這在 Visual Studio 2017 中已變更。 在 Visual Studio 2015 和 Visual Studio 2017 中，C++ 工具組的主要版本號碼為 14 (Visual Studio 2015 為 v140，Visual Studio 2017 為 v141)。 這反映以任一編譯器版本編譯的執行階段程式庫和應用程式大部分為二進位相容的。 這表示您可以在 Visual Studio 2017 中建立 DLL，然後從使用 Visual Studio 2015 編譯的應用程式中取用該 DLL；或是使用含有透過 Visual Studio 2015 工具組建置之應用程式的 Visual Studio 2017 可轉散發程式庫。  

這項規則有兩個例外。 在下列情況下，不保證二進位相容性：  

1) 使用 /GL 編譯器參數編譯靜態程式庫或目的檔時。  

2) 應用程式所取用的可轉散發程式庫版本號碼小於用來編譯應用程式的工具組時。 換句話說，如果您使用平台工具組 v141 編譯程式，應用程式所取用的所有可轉散發程式庫都必須使用 v141 或以上進行編譯。  

## <a name="see-also"></a>請參閱  

[Visual C++ 變更歷程記錄](..\porting\visual-cpp-change-history-2003-2015.md)


