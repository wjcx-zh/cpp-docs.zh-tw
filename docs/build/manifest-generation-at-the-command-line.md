---
title: 命令列的資訊清單產生過程
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493196"
---
# <a name="manifest-generation-at-the-command-line"></a>命令列的資訊清單產生過程

當您使用 nmake 或類似的工具從命令列建立 C/c + + 應用程式時，會在連結器處理所有目的檔並建立最終二進位檔之後，產生資訊清單。 連結器會收集儲存在物件檔中的元件資訊，並將這些資訊結合成最終的資訊清單檔。 根據預設，連結器會產生名為*binary_name*的檔案。描述最終二進位檔的*擴充*功能資訊清單。 連結器不會在二進位檔中內嵌資訊清單檔，而且只能產生資訊清單做為外部檔案。 有數種方式可以將資訊清單內嵌在最後的二進位檔中，例如使用[資訊清單工具（mt.exe）](/windows/win32/sbscs/mt-exe)或將資訊清單編譯成資源檔。 請務必記住，在最後一個二進位檔中內嵌資訊清單時，必須遵循特定規則，以啟用累加連結、簽章和編輯後繼續這類功能。 在命令列上建立時，[如何：在 C/c + + 應用程式中內嵌資訊清單](how-to-embed-a-manifest-inside-a-c-cpp-application.md)中會討論這些和其他選項。

## <a name="see-also"></a>請參閱

[資訊清單](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (以累加方式連結)](reference/incremental-link-incrementally.md)<br/>
[強式名稱元件（元件簽署）（c + +/CLI）](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[編輯後繼續](/visualstudio/debugger/edit-and-continue)<br/>
[瞭解 C/c + + 程式的資訊清單產生](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
