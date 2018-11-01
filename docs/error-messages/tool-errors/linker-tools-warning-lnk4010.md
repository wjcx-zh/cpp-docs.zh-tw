---
title: 連結器工具警告 LNK4010
ms.date: 11/04/2016
f1_keywords:
- LNK4010
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
ms.openlocfilehash: 3f25c9194f48df4064282fb8601928b3ff00f40e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558791"
---
# <a name="linker-tools-warning-lnk4010"></a>連結器工具警告 LNK4010

無效的子系統版本號碼數字，假設預設的子系統版本

您可以指定映像的子系統版本 ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md))。 每個子系統有最低版本需求。 如果指定的版本低於最小值，會發生這個警告，並連結器就會直接使用預設的子系統。