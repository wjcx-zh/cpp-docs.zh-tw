---
title: 用於程式碼分析的 C++ 專案範例
description: 如何創建範例解決方案,用於 Visual Studio 中 Microsoft C++的代碼分析演練。
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372052"
---
# <a name="sample-c-project-for-code-analysis"></a>用於程式碼分析的 C++ 專案範例

以下過程展示如何為演練建立範例[:分析 C/C++缺陷代碼](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)。 這些程序會建立：

- 名為*CppDemo*的視覺工作室解決方案。

- 一個名為*Code缺陷的*靜態庫專案。

- 名為*註解 的*靜態庫專案 。

這些程序也會提供標頭的程式碼，以及用於靜態程式庫的 *.cpp* 檔案。

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>建立 CppDemo 解決方案和 CodeDefects 專案

::: moniker range=">=vs-2019"

1. 打開視覺化工作室並選擇 **"創建新專案**"

1. 在 **「建立新項目**」 對話框中,將語言篩選器更改為**C++**。

1. 選擇**Windows 桌面精靈**並選擇 **「 下一步**」 按鈕。

1. 在「**設定新項目**」 頁上,在 **「專案名稱**」 文字框中, 輸入*程式碼缺陷*。

1. 在 **「解決方案名稱**文字」 框中,輸入*CppDemo*。

1. 選擇 **[建立]**。

1. 在**Windows 桌面項目**對話方塊中,將**應用程式類型**更改為**靜態庫 (.lib)。**

1. 在 [其他選項] **** 下，選取 [空專案] ****。

1. 選擇 **「確定」** 以創建解決方案和專案。

::: moniker-end

::: moniker range="vs-2017"

1. 開啟 Visual Studio。 在選單列上,選擇 **「檔** > **新專案** > **」。。**

1. 在 **「新項目」** 對話框中,**選擇「視覺C++** > **Windows 桌面**」 。

1. 選擇**Windows 桌面精靈**。

1. 在 **「名稱**」 文字框中,輸入*程式碼缺陷*。

1. 在 **「解決方案名稱**文字」 框中,輸入*CppDemo*。

1. 選擇 **"確定**"。

1. 在**Windows 桌面項目**對話方塊中,將**應用程式類型**更改為**靜態庫 (.lib)。**

1. 在 [其他選項] **** 下，選取 [空專案] ****。

1. 選擇 **「確定」** 以創建解決方案和專案。

::: moniker-end

::: moniker range="vs-2015"

1. 開啟 Visual Studio。 在選單列上,選擇 **「檔** > **新專案** > **」。。**

1. 在**新項目**對話框中,**選擇樣本**>**視覺化C++** > **Win32**。

1. 選擇**Win32 主控台應用程式**。

1. 在 **「名稱**」 文字框中,輸入*程式碼缺陷*。

1. 在 **「解決方案名稱**文字」 框中,輸入*CppDemo*。

1. 選擇 **"確定**"。

1. 在**Win32 應用程式精靈**對話框中,選擇 **「下一步**」按鈕。

1. 將**應用程式型態**改變為**靜態庫**。

1. 在 **'其他選項**' 下,取消選擇**預編譯標頭**。

1. 選擇 **「完成」** 以建立解決方案和專案。

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>將標頭和來源檔案新增至 CodeDefects 專案

1. 在解決方案資源管理員中,展開**程式碼缺陷**。

1. 右鍵按一下以打開**標題檔的**上下文選單。 選擇 **「添加新** > **專案**」。

1. 在「**新增新項目」** 對話方塊中,選擇 **「可視C++** > **程式碼**」,然後選擇 **「標題檔 」(.h)。**

1. 在 **「名稱**編輯」框中,輸入*Bug.h,* 然後選擇「**添加**」 按鈕。

1. 在*Bug.h*的編輯視窗中,選擇並刪除內容。

1. 複製以下代碼並將其貼上到編輯器中的*Bug.h*檔中。

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. 在解決方案資源管理器中,右鍵單擊以打開**源檔的**上下文菜單。 選擇 **「添加新** > **專案**」。

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。

1. 在 **「名稱**編輯」框中,輸入*Bug.cpp,* 然後選擇「**添加**」按鈕。

1. 複製以下代碼並將其貼上到編輯器中的*Bug.cpp*檔中。

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. 在選單列上,選擇 **「全部儲存檔** > **Save All**」。

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>新增 Annotations 專案並將其設定為靜態程式庫

::: moniker range=">=vs-2019"

1. 在解決方案資源管理器中,右鍵單擊**CppDemo**以打開上下文菜單。 選擇 **「添加新** > **專案**」。

1. 在「**新增新項目**」 對話框中,選擇**Windows 桌面精靈**,然後選擇 **「 下一步**」 按鈕。

1. 在「**設定新項目**」 頁上,在 **「專案名稱**」文字框中輸入*註釋*,然後選擇「**創建**」 。

1. 在**Windows 桌面項目**對話方塊中,將**應用程式類型**更改為**靜態庫 (.lib)。**

1. 在 [其他選項] **** 下，選取 [空專案] ****。

1. 選擇 **「確定」** 以建立專案。

::: moniker-end

::: moniker range="vs-2017"

1. 在解決方案資源管理器中,右鍵單擊**CppDemo**以打開上下文菜單。 選擇 **「添加新** > **專案**」。

1. 在「**新增新項目」** 對話框中,選擇**視覺C++** > **Windows 桌面**。

1. 選擇**Windows 桌面精靈**。

1. 在 **「名稱**」 文字框中,輸入*註解*,然後選擇 **「確定**」 。

1. 在**Windows 桌面項目**對話方塊中,將**應用程式類型**更改為**靜態庫 (.lib)。**

1. 在 [其他選項] **** 下，選取 [空專案] ****。

1. 選擇 **「確定」** 以建立專案。

::: moniker-end

::: moniker range="vs-2015"

1. 在解決方案資源管理器中,右鍵單擊**CppDemo**以打開上下文菜單。 選擇 **「添加新** > **專案**」。

1. 在 **「新增新項目」** 對話方塊中,**選擇「視覺C++** > **Win32」。。**

1. 選擇**Win32 主控台應用程式**。

1. 在 **「名稱**」 文字框中, 輸入*註解*。

1. 選擇 **"確定**"。

1. 在**Win32 應用程式精靈**對話框中,選擇 **「下一步**」按鈕。

1. 將**應用程式型態**改變為**靜態庫**。

1. 在 **'其他選項**' 下,取消選擇**預編譯標頭**。

1. 選擇 **「完成」** 以建立專案。

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>將標頭檔和來源檔案新增至 Annotations 專案

1. 在解決方案資源管理員中,展開**註解**。

1. 右鍵按一下以在 **「註釋**」下打開**標題檔的**上下文選單。 選擇 **「添加新** > **專案**」。

1. 在「**新增新項目」** 對話方塊中,選擇 **「可視C++** > **程式碼**」,然後選擇 **「標題檔 」(.h)。**

1. 在 **「名稱**編輯」框中,輸入*註解.h,* 然後選擇「**添加**」 按鈕。

1. 在*註解.h*的編輯視窗中,選擇並刪除內容。

1. 複製以下代碼並將其貼上到編輯器中的*註解.h*檔中。

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. 在解決方案資源管理器中,右鍵單擊以在 **「註釋**」下打開**源檔的**上下文菜單。 選擇 **「添加新** > **專案**」。

1. 在 [加入新項目] **** 對話方塊中，選取 [C++ 檔 (.cpp)] ****。

1. 在 **「名稱**編輯」框中,輸入*註釋.cpp,* 然後選擇「**添加**」 按鈕。

1. 複製以下代碼並將其貼上到編輯器中的*註解.cpp*檔中。

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. 在選單列上,選擇 **「全部儲存檔** > **Save All**」。

解決方案現已完成,應生成時無錯誤。

::: moniker range="vs-2017"

> [!NOTE]
> 在 Visual Studio 2017 中`E1097 unknown attribute "no_init_all"`,您可能會在 IntelliSense 引擎中看到虛假警告。 您可以放心地忽略此警告。

::: moniker-end
