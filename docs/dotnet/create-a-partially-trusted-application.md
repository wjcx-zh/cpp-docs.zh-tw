---
title: "如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 編譯器選項 [C++], 部分信任的應用程式"
  - "Interop [C++], 部分信任的應用程式"
  - "互通性 [C++], 部分信任的應用程式"
  - "混合的組件 [C++], 部分信任的應用程式"
  - "msvcm90[d].dll"
  - "部分信任的應用程式 [C++]"
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題討論如何藉由移除 msvcm90.dll 的相依性，以建立使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 之部分信任的 Common Language Runtime 應用程式。  
  
 搭配 **\/clr** 建置的 Visual C\+\+ 用程式須依賴 msvcm90.dll，這個 DLL 屬於 C 執行階段程式庫的一部分。  當您想在部分信任環境中使用應用程式時，CLR 會將特定的程式碼存取安全性規則強制套用在您的 DLL 上。  因此，一定要移除這項相依性，因為 msvcm90.dll 包含機器碼，而且無法對其強制套用程式碼存取安全性原則。  
  
 如果應用程式未使用任何 C 執行階段程式庫功能，而您想要從程式碼中移除對此程式庫的相依性，則必須使用 **\/NODEFAULTLIB:msvcmrt.lib** 連結器選項，並連結到 ptrustm.lib 或 ptrustmd.lib。  這些程式庫包含可以將應用程式初始化和還原初始化的物件檔、初始化程式碼所用的例外狀況類別，以及 Managed 例外處理程式碼。  連結其中一個程式庫將會移除 msvcm90.dll 的相依性。  
  
> [!NOTE]
>  如果應用程式使用 ptrust 程式庫，則其組件解除初始化的順序可能不一樣。  對於一般的應用程式而言，組件的卸載順序通常和載入順序相反，但也不總是如此。  對於部分信任的應用程式而言，組件的卸載順序通常和載入順序相同。  但這一點也同樣不總是成立。  
  
### 建立部分信任的混合型 \(\/clr\) 應用程式  
  
1.  若要移除 msvcm90.dll 的相依性，您必須使用 **\/NODEFAULTLIB:msvcmrt.lib** 連結器選項，指定連結器不要併入此程式庫。  如需關於使用 Visual Studio 開發環境或以程式設計的方式達到此目的的詳細資訊，請參閱 [\/NODEFAULTLIB \(忽略程式庫\)](../build/reference/nodefaultlib-ignore-libraries.md)。  
  
2.  將其中一個 ptrustm 程式庫加入至連結器輸入相依性。  如果您正在發行模式中建置應用程式，請使用 ptrustm.lib。  若為除錯模式，請使用 ptrustmd.lib。  如需關於使用 Visual Studio 開發環境或以程式設計的方式達到此目的的詳細資訊，請參閱 [.Lib 檔做為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。  
  
## 請參閱  
 [混合 \(原生和 Managed\) 組件](../dotnet/mixed-native-and-managed-assemblies.md)   
 [混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)   
 [混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)   
 [\/link \(傳遞選項給連結器\)](../build/reference/link-pass-options-to-linker.md)   
 [機器碼和 .NET Framework 程式碼中的安全性](http://msdn.microsoft.com/zh-tw/bd61be84-c143-409a-a75a-44253724f784)