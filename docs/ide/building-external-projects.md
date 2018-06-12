---
title: 建置外部專案 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b6aa1e5939afe55644df6529bf75ba043f20bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330342"
---
# <a name="building-external-projects"></a>建置外部專案
外部專案是使用 makefile 或其他在 Visual C++ 開發環境外之其他功能的 Visual C++ 專案。  
  
 如果您有外部專案 (例如，makefile 專案)，且想要在 Visual C++ 開發環境中建置，請建立 Makefile 專案，並在 [Makefile 應用程式精靈] 中指定您的專案建置命令和輸出。 如需詳細資訊，請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)。  
  
 請注意，Visual C++ 已不再支援從開發環境中匯出作用中專案 makefile 的能力。 使用 [Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)在命令列建置 Visual Studio 專案。  
  
## <a name="see-also"></a>請參閱  
 [在 Visual Studio 中建置 C++ 專案](../ide/building-cpp-projects-in-visual-studio.md)