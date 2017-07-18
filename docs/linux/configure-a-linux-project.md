---
title: "設定 Linux 專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d7c6adf-54b9-4b23-bd23-5de0c825b768
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 1683c03c522b0b332ced9e93188c65e996ac633d
ms.openlocfilehash: ec7ec2a7f5f0393f00efb6d662494e7be2a3f696
ms.contentlocale: zh-tw
ms.lasthandoff: 03/22/2017

---

# <a name="configure-a-linux-project"></a>設定 Linux 專案

## <a name="general-settings"></a>一般設定
使用 Visual Studio，可以設定 Linux 專案的各種選項。  若要檢視這些選項，請選取 [專案] > [屬性] 功能表，或在方案總管中以滑鼠右鍵按一下專案，然後從操作功能表中選取 [屬性]：

![一般組態](media/settings_general.png)

預設會使用此工具來建置可執行檔 (.out)。  若要建置靜態或動態程式庫，或使用現有 Makefile，請使用 [組態類型] 選項。

## <a name="remote-settings"></a>遠端設定
若要變更遠端 Linux 電腦的相關設定，請選取 [遠端設定] 項目︰

![遠端設定](media/settings_remote.png)

* 若要變更目標 Linux 電腦，請使用 [目標電腦] 項目。  這可讓您選取其中一個先前建立的連線。  若要建立新的項目，請參閱[連線到遠端 Linux 電腦](connect-to-your-remote-linux-computer.md)小節。

* [遠端根目錄] 決定在遠端 Linux 電腦上建置專案的根目錄。  除非進行變更，否則這會預設為 **~/projects**。

* [遠端專案目錄] 是在遠端 Linux 電腦上建置這個特定專案的位置。  這會預設為上面所設定之根目錄下的 **$(RemoteRootDir)/$(ProjectName)**，其會擴充到目前專案後命名的目錄。

* 最後，若要變更預設 C 和 C++ 編譯器，或者使用連結器和封存器來建置專案，請使用 [Tools Defaults]\(工具預設值) 區段中的適當項目。  這些可以設定成使用特定版本的 GCC，甚至 Clang 編譯器 (舉例來說)。

## <a name="vc-directories"></a>VC++ 目錄
根據預設，Visual Studio 不會包含 Linux 電腦中的任何系統層級包含檔案。  例如，Visual Studio 中沒有 **/usr/include** 目錄中的項目。  如需完整 [IntelliSense](/visualstudio/ide/using-intellisense) 支援，您必須將這些檔案複製到開發電腦上的某個位置，並將 Visual Studio 指向這個位置。  其中一個選項是使用 scp (安全複製) 來複製檔案。  在 Windows 10 上，您可以使用 [Bash on Windows](https://msdn.microsoft.com/commandline/wsl/about) 來執行 scp。  針對舊版 Windows，您將使用 [PSCP (PuTTY Secure Copy)](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) 這類項目。

使用與下列類似的命令，即可複製檔案：

`scp -r linux_username@remote_host:/usr/include .`

請務必取代上方適合您自己環境的 **linux_username** 和 **remote_host** 值。

複製檔案之後，請使用 [專案屬性] 中的 [VC++ 目錄] 項目，告訴 Visual Studio 在何處找到剛剛複製的其他包含檔案。

![VC++ 目錄](media/settings_directories.png)

## <a name="copy-sources"></a>複製來源
建置時，會將開發電腦上的來源檔案複製到 Linux 電腦，並在該處進行編譯。  根據預設，Visual Studio 專案中的所有來源都會複製到上方設定中所設定的位置。  不過，也可以在清單中新增其他來源，或者完全關閉複製來源，後者是 Makefile 專案的預設值。

* [要複製的來源] 決定將哪些來源複製到遠端電腦。  根據預設，**@(SourcesToCopyRemotely)** 預設為專案中所有的原始程式碼檔案，但不包括任何資產/資源檔案，例如影像。

* [複製來源] 可以開啟和關閉，以啟用和停用將原始程式檔複製到遠端電腦。

* [要複製的其他來源] 可讓您新增將複製到遠端系統的其他原始程式檔。  您可以指定分號分隔清單，也可以使用 **:=** 語法來指定要使用的本機和遠端名稱︰

  `C:\Projects\ConsoleApplication1\MyFile.cpp:=~/projects/ConsoleApplication1/ADifferentName.cpp;C:\Projects\ConsoleApplication1\MyFile2.cpp:=~/projects/ConsoleApplication1/ADifferentName2.cpp;`

## <a name="build-events"></a>建置事件
因為所有編譯都是在遠端電腦上進行，所以已在 [專案屬性] 的 [建置事件] 區段中新增數個額外建置事件。  這些是 [遠端建置前事件]、[遠端連結前事件] 和 [移除建置後事件]，並且在程序中的個別步驟之前或之後發生於遠端電腦上。

![建置事件](media/settings_buildevents.png)

## <a name="see-also"></a>另請參閱
[使用專案屬性](../ide/working-with-project-properties.md)
