---
title: 在舊版執行階段版本上執行 C++ -clr 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee823d7b37428ea335d5d789a4fcfb4caa673dda
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378047"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>在舊版執行階段版本上執行 C++ /clr 應用程式

除非另行指定，否則 C++ .NET Framework 應用程式已建置為在編譯器用來建置應用程式的 Common Language Runtime (CLR) 版本上執行。 不過，針對一個版本的執行階段所建置的 .exe 應用程式，可以在提供必要功能的任何其他版本上執行。

若要完成這項作業，請提供在 `supportedRuntime` 標記中包含執行階段版本資訊的 app.config 檔案。

在執行階段，app.config 檔案的名稱必須具有格式 *filename.ext*.config，其中 *filename.ext* 是啟動應用程式的可執行檔名稱，而且必須在與可執行檔相同的目錄中。 例如，如果您的應用程式名為 TestApp.exe，app.config 檔案會命名為 TestApp.exe.config。

如果您指定多個執行階段版本，而且應用程式在具有多個已安裝執行階段版本的電腦上執行，則應用程式會使用 config 檔中所指定且已安裝的第一個版本。

## <a name="see-also"></a>請參閱

[部署傳統型應用程式](../ide/deploying-native-desktop-applications-visual-cpp.md)