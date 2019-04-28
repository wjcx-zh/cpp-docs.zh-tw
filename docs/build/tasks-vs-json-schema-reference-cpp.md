---
title: Tasks.vs.json 結構描述參考 (C++)
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315049"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json (C++)

`tasks.vs.json` 檔案可新增至開啟資料夾專案來定義任何任意工作，然後從 [方案總管] 操作功能表叫用它。 CMake 專案通常不會使用此檔案，因為所有的建置命令都已在 `CMakeLists.txt` 中指定。 針對 CMake 之外的其他組建系統，此處是您指定建置命令及叫用建置指令碼的位置。 如需使用 tasks.vs.json 的一般資訊，請參閱[針對「開啟資料夾」開發自訂建置及偵錯工作](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

