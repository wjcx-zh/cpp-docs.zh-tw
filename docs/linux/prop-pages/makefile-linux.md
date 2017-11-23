---
title: "一般屬性 (Linux C++ Makefile 專案)| Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: 9507ab2ed54d8160afdd8071b0779b51d6802bef
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="makefile-project-properties-linux-c"></a>MakeFile 專案屬性 (Linux C++)
此為 Linux Makefile 專案中可用屬性的部分清單。 許多 Makefile 專案的屬性皆相同 

## <a name="general"></a>一般
屬性 | 說明 | 選擇
--- | ---| ---
輸出目錄 | 指定輸出檔案目錄的相對路徑；可包含環境變數。
中繼目錄 | 指定中繼檔案目錄的相對路徑；可包含環境變數。
建置記錄檔 | 指定啟用組建記錄時，要寫入的組建記錄檔。
組態類型 | 指定此組態所產生的輸出類型。 | **動態程式庫 (.so)** - 動態程式庫 (.so)<br>**靜態程式庫 (.a)** - 靜態程式庫 (.a)<br>**應用程式 (.out)** - 應用程式 (.out)<br>**Makefile** - Makefile<br>
遠端組建電腦 | 要用於遠端建置、部署及偵錯的目標電腦或裝置。
遠端組建根目錄 | 指定遠端電腦或裝置上的目錄路徑。
遠端組建專案目錄 | 指定專案在遠端電腦或裝置上的目錄路徑。

## <a name="debugging"></a>偵錯
請參閱[偵錯工具屬性 (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>複製來源
請參閱[複製來源專案屬性 (Linux C++)](copy-sources-project.md)。

## <a name="build-events"></a>建置事件

### <a name="pre-build-event"></a>建置前事件
屬性 | 說明
--- | ---
命令列 | 指定要執行建置前事件工具的命令列。
說明 | 指定要顯示的建置前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

### <a name="post-build-event"></a>建置後事件
命令列 | 指定執行建置後事件工具的命令列。
命令列 | 指定要顯示的建置後事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

### <a name="remote-pre-build-event"></a>遠端建置前事件
命令列 | 指定在遠端系統上執行建置前事件工具的命令列。
描述 | 指定要顯示的建置前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 您也可以使用下列類型的語法，將清單提供為遠端到本機的對應配對：fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2，便可將遠端檔案複製到本機電腦上的指定位置。

### <a name="remote-post-build-event"></a>遠端建置後事件
命令列 | 指定在遠端系統上執行建置後事件工具的命令列。
命令列 | 指定要顯示的建置後事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 您也可以使用下列類型的語法，將清單提供為遠端到本機的對應配對：fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2，便可將遠端檔案複製到本機電腦上的指定位置。

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense
可在專案或檔案層級設定 IntelliSense 屬性，來提供 IntelliSense 引擎的線索。 它們不會影響編譯。

屬性 | 說明
--- | ---
Include 搜尋路徑 | 指定內含的搜尋路徑，以解析內含的檔案。
強制內含 | 指定要強制內含的檔案。
前置處理器定義 | 指定來源檔案所使用的前置處理器定義。
取消前置處理器的定義 | 指定取消一或多個前置處理器的定義。     (/U[巨集])
其他選項 | 指定在剖析 C++ 檔案時，Intellisense 要使用的其他編譯器參數。

### <a name="build"></a>組建
屬性 | 說明
--- | ---
Build 命令列 | 指定執行 'Build' 命令的命令列。
Rebuild All 命令列 | 指定執行 'Rebuild All' 命令的命令列。
Clean 命令列 | 指定執行 'Clean' 命令的命令列。

### <a name="remote-build"></a>遠端組建
屬性 | 說明
--- | ---
Build 命令列 | 指定執行 'Build' 命令的命令列。 其會於遠端系統上執行。
Rebuild All 命令列 | 指定執行 'Rebuild All' 命令的命令列。 其會於遠端系統上執行。
Clean 命令列 | 指定執行 'Clean' 命令的命令列。 其會於遠端系統上執行。
輸出 | 指定遠端組建於遠端系統上所產生的輸出。

