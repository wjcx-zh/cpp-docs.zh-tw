---
title: 遠端建置事件 (Linux C++)
ms.date: 06/07/2019
ms.assetid: 165d3690-5bd8-4b0b-bc66-8b699d85a61b
ms.openlocfilehash: 4a3e9019d4dacc3d494feb5d6de8f5c2247e4d12
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441506"
---
# <a name="build-event-properties-linux-c"></a>建置事件屬性 (Linux C++)

::: moniker range="vs-2015"

Visual Studio 2017 及更新版本支援 Linux。

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="pre-build-event"></a>建置前事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定要執行建置前事件工具的命令列。 |
| 描述 | 指定要顯示的建置前事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 選擇性地使用類似如下的語法來指定遠端對應配對的本機： fulllocalpath1： = fullremotepath1; fulllocalpath2： = fullremotepath2，其中本機檔案可以複製到遠端系統上指定的遠端位置。 |

## <a name="pre-link-event"></a>連結前事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定要執行連結前事件工具的命令列。 |
| 描述 | 指定要顯示的連結前事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 選擇性地使用類似如下的語法來指定遠端對應配對的本機： fulllocalpath1： = fullremotepath1; fulllocalpath2： = fullremotepath2，其中本機檔案可以複製到遠端系統上指定的遠端位置。 |

## <a name="post-build-event"></a>建置後事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定要執行建置後事件工具的命令列。 |
| 描述 | 指定要顯示的建置後事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要複製到遠端系統的其他檔案。 選擇性地使用類似如下的語法來指定遠端對應配對的本機： fulllocalpath1： = fullremotepath1; fulllocalpath2： = fullremotepath2，其中本機檔案可以複製到遠端系統上指定的遠端位置。 |

## <a name="remote-pre-build-event"></a>遠端建置前事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定在遠端系統上執行建置前事件工具的命令列。 |
| 描述 | 指定要顯示的建置前事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 選擇性地使用類似如下的語法來指定遠端至本機對應組： fullremotepath1： = fulllocalpath1; fullremotepath2： = fulllocalpath2，其中遠端檔案可以複製到本機電腦上的指定位置。 |

## <a name="remote-pre-link-event"></a>遠端連結前事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定在遠端系統上執行連結前事件工具的命令列。 |
| 描述 | 指定要顯示的連結前事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 選擇性地使用類似如下的語法來指定遠端至本機對應組： fullremotepath1： = fulllocalpath1; fullremotepath2： = fulllocalpath2，其中遠端檔案可以複製到本機電腦上的指定位置。 |

## <a name="remote-post-build-event"></a>遠端建置後事件

| 屬性 | 描述 |
|--|--|
| 命令列 | 指定在遠端系統上執行建置後事件工具的命令列。 |
| 描述 | 指定要顯示的建置後事件工具描述。 |
| 使用於組建中 | 指定是否要將此建置事件排除在目前組態的建置之外。 |
| 要複製的其他檔案 | 指定要從遠端系統複製的其他檔案。 選擇性地使用類似如下的語法來指定遠端至本機對應組： fullremotepath1： = fulllocalpath1; fullremotepath2： = fulllocalpath2，其中遠端檔案可以複製到本機電腦上的指定位置。 |

::: moniker-end
