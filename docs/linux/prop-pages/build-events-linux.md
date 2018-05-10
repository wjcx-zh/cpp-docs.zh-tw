---
title: 遠端建置事件 (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 38c036bf747115823b853d0d66077f4402a7f7ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="build-event-properties-linux-c"></a>建置事件屬性 (Linux C++) 

## <a name="pre-build-event"></a>建置前事件

屬性 | 描述
--- | ---
命令列 | 指定要執行建置前事件工具的命令列。
描述 | 指定要顯示的建置前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

## <a name="pre-link-event"></a>連結前事件

屬性 | 描述
--- | ---
命令列 | 指定要執行連結前事件工具的命令列。
描述 | 指定要顯示的連結前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

## <a name="post-build-event"></a>建置後事件

屬性 | 描述
--- | ---
命令列 | 指定要執行建置後事件工具的命令列。
描述 | 指定要顯示的建置後事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 您也可以使用類似如下的語法，將清單提供為本機到遠端的對應配對：fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2，如此會將本機檔案複製到遠端系統上指定的遠端位置。

## <a name="remote-pre-build-event"></a>遠端建置前事件

屬性 | 描述
--- | ---
命令列 | 指定在遠端系統上執行建置前事件工具的命令列。
描述 | 指定要顯示的建置前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 您也可以使用下列類型的語法，將清單提供為遠端到本機的對應配對：fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2，便可將遠端檔案複製到本機電腦上的指定位置。

## <a name="remote-pre-link-event"></a>遠端連結前事件

屬性 | 描述
--- | ---
命令列 | 指定在遠端系統上執行連結前事件工具的命令列。
描述 | 指定要顯示的連結前事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 您也可以使用下列類型的語法，將清單提供為遠端到本機的對應配對：fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2，如此會將遠端檔案複製到本機電腦上的指定位置。

## <a name="remote-post-build-event"></a>遠端建置後事件

屬性 | 描述
--- | ---
命令列 | 指定在遠端系統上執行建置後事件工具的命令列。
描述 | 指定要顯示的建置後事件工具描述。
使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。
要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 您也可以使用下列類型的語法，將清單提供為遠端到本機的對應配對：fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2，如此會將遠端檔案複製到本機電腦上的指定位置。
