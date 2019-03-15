---
title: Tasks.vs.json 結構描述參考 （c + +）
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824740"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json （c + +）

A`tasks.vs.json`檔案可以加入至開啟資料夾 」 專案，以定義任何任意的工作，並接著將它從叫用**方案總管 中**操作功能表。 CMake 專案通常不會使用此檔案中所指定的所有建置命令因為`CMakeLists.txt`。 適用於 CMake 以外的組建系統，這是您可以在此指定建置命令，並叫用組建指令碼。 如需使用 tasks.vs.json 的一般資訊，請參閱 <<c0> [ 自訂建置及偵錯開發 「 開啟資料夾 」 工作](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio)。

