---
title: 在 Visual Studio 中建立新的 C++ Linux 專案 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 186789a94186621d2ec0103cb24dfdc17b0420cc
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410677"
---
# <a name="create-a-new-linux-project"></a>建立新的 Linux 專案

首先，請確定您已安裝適用於 Visual Studio 的 **Linux 開發工作負載**。 如需詳細資訊，請參閱[下載、安裝及設定 Linux 工作負載](download-install-and-setup-the-linux-development-workload.md)。

在 Visual Studio 中為 Linux 編寫 C++ 程式碼時，您可以選擇建立 Visual Studio 專案或 CMake 專案。 本主題描述如何建立 Visual Studio 專案。 如需 CMake 專案的資訊，請參閱[設定 Linux CMake 專案](cmake-linux-project.md)。

若要在 Visual Studio 中建立新的 Linux 專案，請執行下列動作：

1. 在 Visual Studio 中選取 [檔案] > [新增專案]，或按 **Ctrl+Shift+N**。
1. 選取 [Visual C++] > [跨平台] > [Linux] 節點，然後選取您要建立的專案類型、輸入「名稱/位置」並按一下 [確定]。

   ![新的 Linux 專案](media/newproject.png)

   | 專案類型 | 描述
   | ------------ | ---
   | **閃爍 (Raspberry)**           | 以 Raspberry Pi 裝置為目標的專案，並撰寫範例程式碼讓 LED 閃爍
   | **主控台應用程式 (Linux)** | 以任何 Linux 電腦為目標的專案，並撰寫範例程式碼以將文字輸出至主控台
   | **空專案 (Linux)**       | 以任何 Linux 電腦為目標的專案，但未撰寫任何範例程式碼
   | **Makefile 專案 (Linux)**    | 以任何使用標準 Makefile 建置系統所建置之 Linux 電腦為目標的專案

