---
title: 在命令列產生資訊清單 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e2bb423deb4a50da0cf0772ae81e19bb4b48eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220723"
---
# <a name="manifest-generation-at-the-command-line"></a>命令列的資訊清單產生過程
當建置 C/c + + 應用程式，從命令列使用 nmake 或類似工具，連結器已處理所有目的檔，並建置最終二進位檔之後，就是會產生資訊清單。 連結器會收集儲存在目的檔中的組件資訊，並結合成最終的資訊清單檔案的這項資訊。 根據預設，連結器會產生檔案，名為 < binary_name >。\<擴充功能 > 以描述最終二進位檔。 連結器不會內嵌於二進位檔的資訊清單檔，並只會產生資訊清單中的，外部檔案。 有數種方式可內嵌於最終的二進位檔，例如使用資訊清單[資訊清單工具 (mt.exe)](https://msdn.microsoft.com/library/aa375649)或編譯成資源檔的資訊清單。 請務必記住，特定的規則有內嵌於最終的二進位檔，以啟用累加連結，這類功能的資訊清單時所需遵循簽章，以及編輯後繼續。 中會討論這些和其他選項[如何： 將內嵌資訊清單內工作 C/c + + 應用程式](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md)命令列上建置時。  
  
## <a name="see-also"></a>另請參閱  
 [資訊清單](https://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL （以累加方式連結）](../build/reference/incremental-link-incrementally.md)   
 [強式名稱組件 （組件簽署） (C + + /cli CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [編輯後繼續](/visualstudio/debugger/edit-and-continue)   
 [了解 C/C++ 程式的資訊清單產生過程](../build/understanding-manifest-generation-for-c-cpp-programs.md)