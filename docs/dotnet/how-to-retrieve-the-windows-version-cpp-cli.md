---
title: 如何： 擷取 Windows 版本 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
ms.assetid: 7e6f567b-d378-49bb-aa59-2240f69a022d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bf602bd9fbd0765c54f9955fbb2cfcc3588e96dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-windows-version-ccli"></a>如何：擷取 Windows 版本 (C++/CLI)
下列程式碼範例示範如何擷取目前的作業系統的平台和版本資訊。 這項資訊會儲存在<xref:System.Environment.OSVersion%2A?displayProperty=fullName>屬性組成廣泛條款中描述的 Windows 版本的列舉和<xref:System.Environment.Version%2A>物件，其中包含作業系統的確切的組建。  
  
## <a name="example"></a>範例  
  
```  
// os_ver.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   OperatingSystem^ osv = Environment::OSVersion;  
   PlatformID id = osv->Platform;  
   Console::Write("Operating system: ");  
  
   if (id == PlatformID::Win32NT)  
      Console::WriteLine("Win32NT");  
   else if (id == PlatformID::Win32S)  
      Console::WriteLine("Win32S");  
   else if (id == PlatformID::Win32Windows)  
      Console::WriteLine("Win32Windows");  
   else  
      Console::WriteLine("WinCE");  
  
   Version^ version = osv->Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write("OS Version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
                   build, major, minor, revision);  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Windows 作業 (C + + /CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)