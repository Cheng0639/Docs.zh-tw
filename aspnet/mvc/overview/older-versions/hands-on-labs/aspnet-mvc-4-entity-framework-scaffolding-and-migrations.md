---
uid: mvc/overview/older-versions/hands-on-labs/aspnet-mvc-4-entity-framework-scaffolding-and-migrations
title: "ASP.NET MVC 4 Entity Framework Scaffolding 和移轉 |Microsoft 文件"
author: rick-anderson
description: "如果您已熟悉 ASP.NET MVC 4 控制器方法，或已完成&quot;Helper、 表單和驗證&quot;實際操作實驗室中，您應該注意..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/18/2013
ms.topic: article
ms.assetid: 093c1362-f10b-407c-a708-be370f4b62b0
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions/hands-on-labs/aspnet-mvc-4-entity-framework-scaffolding-and-migrations
msc.type: authoredcontent
ms.openlocfilehash: 15db1589eb90739458b430c35cea38e93e3dec5a
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2017
---
<a name="aspnet-mvc-4-entity-framework-scaffolding-and-migrations"></a><span data-ttu-id="d6f2f-103">ASP.NET MVC 4 Entity Framework Scaffolding 和移轉</span><span class="sxs-lookup"><span data-stu-id="d6f2f-103">ASP.NET MVC 4 Entity Framework Scaffolding and Migrations</span></span>
====================
<span data-ttu-id="d6f2f-104">由[Web 營小組](https://twitter.com/webcamps)</span><span class="sxs-lookup"><span data-stu-id="d6f2f-104">by [Web Camps Team](https://twitter.com/webcamps)</span></span>

> <span data-ttu-id="d6f2f-105">如果您已熟悉 ASP.NET MVC 4 控制器方法，或已完成&quot;Helper、 表單和驗證&quot;實際操作實驗室中，您應該注意許多邏輯，以建立、 更新、 列出及移除它會重複任何資料實體在應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-105">If you are familiar with ASP.NET MVC 4 controller methods, or have completed the &quot;Helpers, Forms and Validation&quot; Hands-On lab, you should be aware that many of the logic to create, update, list and remove any data entity it is repeated among the application.</span></span> <span data-ttu-id="d6f2f-106">更別說，如果您的模型有數個類別以管理，您將會有可能要花很長的時間，寫入每個實體作業，以及每個檢視的 POST 與 GET 動作方法。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-106">Not to mention that, if your model has several classes to manipulate, you will be likely to spend a considerable time writing the POST and GET action methods for each entity operation, as well as each of the views.</span></span>
> 
> <span data-ttu-id="d6f2f-107">在這個實驗室中，您將學習如何使用 ASP.NET MVC 4 scaffolding 自動產生應用程式的 CRUD （建立、 讀取、 更新和刪除） 的基準線。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-107">In this lab you will learn how to use the ASP.NET MVC 4 scaffolding to automatically generate the baseline of your application's CRUD (Create, Read, Update and Delete).</span></span> <span data-ttu-id="d6f2f-108">從開始從簡單的模型類別，並不需要撰寫一行程式碼，您將建立一個控制站，會包含所有 CRUD 作業，以及所有必要的檢視。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-108">Starting from a simple model class, and, without writing a single line of code, you will create a controller that will contain all the CRUD operations, as well as the all the necessary views.</span></span> <span data-ttu-id="d6f2f-109">在建置及執行簡單的解決方案之後，您必須產生，以及 MVC 邏輯和資料管理檢視的應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-109">After building and running the simple solution, you will have the application database generated, together with the MVC logic and views for data manipulation.</span></span>
> 
> <span data-ttu-id="d6f2f-110">此外，您將學習使用 Entity Framework 移轉執行整個應用程式模型更新是多麼的輕鬆。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-110">In addition, you will learn how easy it is to use Entity Framework Migrations to perform model updates throughout your entire application.</span></span> <span data-ttu-id="d6f2f-111">Entity Framework 移轉可讓您的模型已變更執行簡單的步驟之後，修改您的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-111">Entity Framework Migrations will let you modify your database after the model has changed with simple steps.</span></span> <span data-ttu-id="d6f2f-112">進行所有這些動作記住，您將能夠建立及維護的 web 應用程式更有效率地運用 ASP.NET MVC 4 的最新的功能。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-112">With all these in mind, you will be able to build and maintain web applications more efficiently, taking advantage of the latest features of ASP.NET MVC 4.</span></span>


<a id="Objectives"></a>

<a id="Objectives"></a>
### <a name="objectives"></a><span data-ttu-id="d6f2f-113">目標</span><span class="sxs-lookup"><span data-stu-id="d6f2f-113">Objectives</span></span>

<span data-ttu-id="d6f2f-114">在這個實際操作實驗室中，您將學會如何：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-114">In this Hands-On Lab, you will learn how to:</span></span>

- <span data-ttu-id="d6f2f-115">使用 ASP.NET scaffolding 控制站的 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-115">Use ASP.NET scaffolding for CRUD operations in controllers.</span></span>
- <span data-ttu-id="d6f2f-116">變更使用 Entity Framework 移轉的資料庫模型。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-116">Change the database model using Entity Framework Migrations.</span></span>

<a id="Prerequisites"></a>

<a id="Prerequisites"></a>
### <a name="prerequisites"></a><span data-ttu-id="d6f2f-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="d6f2f-117">Prerequisites</span></span>

<span data-ttu-id="d6f2f-118">您必須具備下列項目才能完成本實驗室：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-118">You must have the following items to complete this lab:</span></span>

- <span data-ttu-id="d6f2f-119">[Microsoft Visual Studio Express 2012 for Web](https://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web)或上層 (讀取[附錄 A](#AppendixA)如需有關如何安裝指示)。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-119">[Microsoft Visual Studio Express 2012 for Web](https://www.microsoft.com/visualstudio/eng/products/visual-studio-express-for-web) or superior (read [Appendix A](#AppendixA) for instructions on how to install it).</span></span>

<a id="Setup"></a>

<a id="Setup"></a>
### <a name="setup"></a><span data-ttu-id="d6f2f-120">安裝程式</span><span class="sxs-lookup"><span data-stu-id="d6f2f-120">Setup</span></span>

<span data-ttu-id="d6f2f-121">**安裝程式碼片段**</span><span class="sxs-lookup"><span data-stu-id="d6f2f-121">**Installing Code Snippets**</span></span>

<span data-ttu-id="d6f2f-122">為了方便起見，大部分您將沿著這個實驗室管理的程式碼可做為 Visual Studio 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-122">For convenience, much of the code you will be managing along this lab is available as Visual Studio code snippets.</span></span> <span data-ttu-id="d6f2f-123">若要安裝執行的程式碼片段**.\Source\Setup\CodeSnippets.vsi**檔案。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-123">To install the code snippets run **.\Source\Setup\CodeSnippets.vsi** file.</span></span>

<span data-ttu-id="d6f2f-124">如果您不熟悉 Visual Studio 程式碼片段，而且想来了解如何使用它們，您可以從這份文件參考附錄&quot;[附錄 b： 使用程式碼片段](#AppendixB)&quot;。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-124">If you are not familiar with the Visual Studio Code Snippets, and want to learn how to use them, you can refer to the appendix from this document &quot;[Appendix B: Using Code Snippets](#AppendixB)&quot;.</span></span>

* * *

<a id="Exercises"></a>

<a id="Exercises"></a>
## <a name="exercises"></a><span data-ttu-id="d6f2f-125">練習</span><span class="sxs-lookup"><span data-stu-id="d6f2f-125">Exercises</span></span>

<span data-ttu-id="d6f2f-126">下列練習構成這個實際操作實驗室：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-126">The following exercise make up this Hands-On Lab:</span></span>

1. [<span data-ttu-id="d6f2f-127">使用 ASP.NET MVC 4 Scaffolding 與 Entity Framework 移轉</span><span class="sxs-lookup"><span data-stu-id="d6f2f-127">Using ASP.NET MVC 4 Scaffolding with Entity Framework Migrations</span></span>](#Exercise1)

> [!NOTE]
> <span data-ttu-id="d6f2f-128">這個練習會伴隨著**結束**包含所產生的解決方案，您必須先完成本練習之後取得資料夾。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-128">This exercise is accompanied by an **End** folder containing the resulting solution you should obtain after completing the exercise.</span></span> <span data-ttu-id="d6f2f-129">如果您需要其他協助逐步練習，您可以使用這個方案做為指南。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-129">You can use this solution as a guide if you need additional help working through the exercise.</span></span>


<span data-ttu-id="d6f2f-130">完成本實驗室估計時間： **30 分鐘**</span><span class="sxs-lookup"><span data-stu-id="d6f2f-130">Estimated time to complete this lab: **30 minutes**</span></span>

<a id="Exercise1"></a>

<a id="Exercise_1_Using_ASPNET_MVC_4_Scaffolding_with_Entity_Framework_Migrations"></a>
### <a name="exercise-1-using-aspnet-mvc-4-scaffolding-with-entity-framework-migrations"></a><span data-ttu-id="d6f2f-131">練習 1： 使用 ASP.NET MVC 4 Scaffolding 與 Entity Framework 移轉</span><span class="sxs-lookup"><span data-stu-id="d6f2f-131">Exercise 1: Using ASP.NET MVC 4 Scaffolding with Entity Framework Migrations</span></span>

<span data-ttu-id="d6f2f-132">ASP.NET MVC scaffolding 提供快速的方法來產生 CRUD 作業的標準化方式，建立必要的邏輯，可讓您的應用程式與資料庫層級互動。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-132">ASP.NET MVC scaffolding provides a quick way to generate the CRUD operations in a standardized way, creating the necessary logic that lets your application interact with the database layer.</span></span>

<span data-ttu-id="d6f2f-133">在此練習中，您將學習如何使用 ASP.NET MVC 4 scaffolding 程式碼第一次建立 CRUD 方法。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-133">In this exercise, you will learn how to use ASP.NET MVC 4 scaffolding with code first to create the CRUD methods.</span></span> <span data-ttu-id="d6f2f-134">然後，您將學習如何更新資料庫中的變更套用使用 Entity Framework 移轉您的模型。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-134">Then, you will learn how to update your model applying the changes in the database by using Entity Framework Migrations.</span></span>

<a id="Ex1Task1"></a>

<a id="Task_1-_Creating_a_new_ASPNET_MVC_4_project_using_Scaffolding"></a>
#### <a name="task-1--creating-a-new-aspnet-mvc-4-project-using-scaffolding"></a><span data-ttu-id="d6f2f-135">工作 1-建立新的 ASP.NET MVC 4 專案使用 Scaffolding</span><span class="sxs-lookup"><span data-stu-id="d6f2f-135">Task 1- Creating a new ASP.NET MVC 4 project using Scaffolding</span></span>

1. <span data-ttu-id="d6f2f-136">如果尚未開啟，啟動**Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-136">If not already open, start **Visual Studio 2012**.</span></span>
2. <span data-ttu-id="d6f2f-137">選取**檔案 |新的專案**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-137">Select **File | New Project**.</span></span> <span data-ttu-id="d6f2f-138">在 [新增專案] 對話方塊中，在**Visual C# |Web**區段中，選取**ASP.NET MVC 4 Web 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-138">In the New Project dialog, under the **Visual C# | Web** section, select **ASP.NET MVC 4 Web Application**.</span></span> <span data-ttu-id="d6f2f-139">若要將專案命名**MVC4andEFMigrations**並將位置設定為**Source\Ex1 UsingMVC4ScaffoldingEFMigrations**本實驗室的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-139">Name the project to **MVC4andEFMigrations** and set the location to **Source\Ex1-UsingMVC4ScaffoldingEFMigrations** folder of this lab.</span></span> <span data-ttu-id="d6f2f-140">設定**方案名稱**至**開始**，並確定**為方案建立目錄**已核取。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-140">Set the **Solution name** to **Begin** and ensure **Create directory for solution** is checked.</span></span> <span data-ttu-id="d6f2f-141">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-141">Click **OK**.</span></span>

    <span data-ttu-id="d6f2f-142">![新 ASP.NET MVC 4 專案 對話方塊](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image1.png "新 ASP.NET MVC 4 專案 對話方塊")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-142">![New ASP.NET MVC 4 Project Dialog Box](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image1.png "New ASP.NET MVC 4 Project Dialog Box")</span></span>

    <span data-ttu-id="d6f2f-143">*新增 ASP.NET MVC 4 專案對話方塊*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-143">*New ASP.NET MVC 4 Project Dialog Box*</span></span>
3. <span data-ttu-id="d6f2f-144">在**新增 ASP.NET MVC 4 專案**對話方塊中，選取**網際網路應用程式**範本，並確定**Razor**是所選**檢視引擎**.</span><span class="sxs-lookup"><span data-stu-id="d6f2f-144">In the **New ASP.NET MVC 4 Project** dialog box select the **Internet Application** template, and make sure that **Razor** is the selected **View engine**.</span></span> <span data-ttu-id="d6f2f-145">按一下**確定**建立專案。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-145">Click **OK** to create the project.</span></span>

    <span data-ttu-id="d6f2f-146">![新的 ASP.NET MVC 4 網際網路應用程式](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image2.png "新 ASP.NET MVC 4 網際網路應用程式")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-146">![New ASP.NET MVC 4 Internet Application](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image2.png "New ASP.NET MVC 4 Internet Application")</span></span>

    <span data-ttu-id="d6f2f-147">*新的 ASP.NET MVC 4 網際網路應用程式*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-147">*New ASP.NET MVC 4 Internet Application*</span></span>
4. <span data-ttu-id="d6f2f-148">在 [方案總管] 中，以滑鼠右鍵按一下**模型**選取**新增 |類別**建立簡單的類別個人 (POCO)。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-148">In the Solution Explorer, right-click **Models** and select **Add | Class** to create a simple class person (POCO).</span></span> <span data-ttu-id="d6f2f-149">命名**人員**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-149">Name it **Person** and click **OK**.</span></span>
5. <span data-ttu-id="d6f2f-150">開啟 Person 類別，並插入下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-150">Open the Person class and insert the following properties.</span></span>

    <span data-ttu-id="d6f2f-151">(程式碼片段- *ASP.NET MVC 4 和實體架構移轉 Ex1 人員屬性*)</span><span class="sxs-lookup"><span data-stu-id="d6f2f-151">(Code Snippet - *ASP.NET MVC 4 and Entity Framework Migrations - Ex1 Person Properties*)</span></span>


    [!code-csharp[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample1.cs)]
6. <span data-ttu-id="d6f2f-152">按一下**建置 |建置方案**以儲存變更，並建置專案。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-152">Click **Build | Build Solution** to save the changes and build the project.</span></span>

    <span data-ttu-id="d6f2f-153">![建置應用程式](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image3.png "建置應用程式")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-153">![Building the application](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image3.png "Building the application")</span></span>

    <span data-ttu-id="d6f2f-154">*建置應用程式*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-154">*Building the Application*</span></span>
7. <span data-ttu-id="d6f2f-155">在 [方案總管] 中，以滑鼠右鍵按一下 [控制器] 資料夾，然後選取**新增 |控制器**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-155">In the Solution Explorer, right-click the controllers folder and select **Add | Controller**.</span></span>
8. <span data-ttu-id="d6f2f-156">控制器*PersonController*並完成**Scaffolding 選項**具有下列值。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-156">Name the controller *PersonController* and complete the **Scaffolding options** with the following values.</span></span>

    1. <span data-ttu-id="d6f2f-157">在**範本**下拉式清單中，選取**具有讀取/寫入動作和檢視表、 使用 Entity Framework 的 MVC 控制器**選項。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-157">In the **Template** drop-down list, select the **MVC controller with read/write actions and views, using Entity Framework** option.</span></span>
    2. <span data-ttu-id="d6f2f-158">在**模型類別**下拉式清單中，選取**人員**類別。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-158">In the **Model class** drop-down list, select the **Person** class.</span></span>
    3. <span data-ttu-id="d6f2f-159">在**資料內容類別**清單中，選取**&lt;新的資料內容...&gt;**.</span><span class="sxs-lookup"><span data-stu-id="d6f2f-159">In the **Data Context class** list, select **&lt;New data context...&gt;**.</span></span> <span data-ttu-id="d6f2f-160">選擇的任何名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-160">Choose any name and click **OK**.</span></span>
    4. <span data-ttu-id="d6f2f-161">在**檢視**下拉式清單中，請確定**Razor**已選取。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-161">In the **Views** drop-down list, make sure that **Razor** is selected.</span></span>

    <span data-ttu-id="d6f2f-162">![新增人員控制器的 scaffolding](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image4.png "加入 scaffolding 人員控制器")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-162">![Adding the Person controller with scaffolding](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image4.png "Adding the Person controller with scaffolding")</span></span>

    <span data-ttu-id="d6f2f-163">*新增人員控制器的 scaffolding*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-163">*Adding the Person controller with scaffolding*</span></span>
9. <span data-ttu-id="d6f2f-164">按一下**新增**scaffolding 人員建立新的控制站。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-164">Click **Add** to create the new controller for Person with scaffolding.</span></span> <span data-ttu-id="d6f2f-165">現在您已經有產生控制器動作，以及檢視。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-165">You have now generated the controller actions as well as the views.</span></span>

    <span data-ttu-id="d6f2f-166">![使用 scaffolding 建立人員控制站之後](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image5.png "使用 scaffolding 建立人員控制站之後")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-166">![After creating the Person controller with scaffolding](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image5.png "After creating the Person controller with scaffolding")</span></span>

    <span data-ttu-id="d6f2f-167">*使用 scaffolding 建立人員控制站之後*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-167">*After creating the Person controller with scaffolding*</span></span>
10. <span data-ttu-id="d6f2f-168">開啟**PersonController**類別。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-168">Open **PersonController** class.</span></span> <span data-ttu-id="d6f2f-169">請注意，已自動產生完整的 CRUD 動作方法。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-169">Notice that the full CRUD action methods have been generated automatically.</span></span>

    <span data-ttu-id="d6f2f-170">![內部的人員控制站](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image6.png "內人員控制站")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-170">![Inside the Person controller](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image6.png "Inside the Person controller")</span></span>

    <span data-ttu-id="d6f2f-171">*內部的人員控制站*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-171">*Inside the Person controller*</span></span>

<a id="Ex1Task2"></a>

<a id="Task_2-_Running_the_application"></a>
#### <a name="task-2--running-the-application"></a><span data-ttu-id="d6f2f-172">工作 2-執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d6f2f-172">Task 2- Running the application</span></span>

<span data-ttu-id="d6f2f-173">此時，資料庫尚未建立。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-173">At this point, the database is not yet created.</span></span> <span data-ttu-id="d6f2f-174">在這項工作，您將會執行第一次應用程式，並測試 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-174">In this task, you will run the application for the first time and test the CRUD operations.</span></span> <span data-ttu-id="d6f2f-175">使用 Code First 立即將會建立此資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-175">The database will be created on the fly with Code First.</span></span>

1. <span data-ttu-id="d6f2f-176">按 **F5** 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-176">Press **F5** to run the application.</span></span>
2. <span data-ttu-id="d6f2f-177">在瀏覽器中，加入**/Person**至 URL，以開啟 [人員] 頁面。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-177">In the browser, add **/Person** to the URL to open the Person page.</span></span>

    <span data-ttu-id="d6f2f-178">![第一次執行的應用程式](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image7.png "第一次執行的應用程式")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-178">![Application first run](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image7.png "Application first run")</span></span>

    <span data-ttu-id="d6f2f-179">*第一次執行應用程式：*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-179">*Application: first run*</span></span>
3. <span data-ttu-id="d6f2f-180">現在，您會瀏覽的人員頁面，並測試 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-180">You will now explore the Person pages and test the CRUD operations.</span></span>

    1. <span data-ttu-id="d6f2f-181">按一下**新建**来加入新的人員。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-181">Click **Create New** to add a new person.</span></span> <span data-ttu-id="d6f2f-182">輸入的名字和姓氏，然後按一下**建立**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-182">Enter a first name and a last name and click **Create**.</span></span>

        <span data-ttu-id="d6f2f-183">![加入新的個人](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image8.png "加入新的人員")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-183">![Adding a new person](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image8.png "Adding a new person")</span></span>

        <span data-ttu-id="d6f2f-184">*加入新的人員*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-184">*Adding a new person*</span></span>
    2. <span data-ttu-id="d6f2f-185">在清單中的人員，您可以刪除、 編輯或加入項目。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-185">In the person's list, you can delete, edit or add items.</span></span>

        <span data-ttu-id="d6f2f-186">![人員清單](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image9.png "人員清單")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-186">![person list](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image9.png "person list")</span></span>

        <span data-ttu-id="d6f2f-187">*人員清單*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-187">*Person list*</span></span>
    3. <span data-ttu-id="d6f2f-188">按一下**詳細資料**以開啟該人員的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-188">Click **Details** to open the person's details.</span></span>

        <span data-ttu-id="d6f2f-189">![人員的詳細資料](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image10.png "人員的詳細資料")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-189">![Person's details](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image10.png "Person's details")</span></span>

        <span data-ttu-id="d6f2f-190">*人員的詳細資料*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-190">*Person's details*</span></span>
4. <span data-ttu-id="d6f2f-191">關閉瀏覽器，並返回 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-191">Close the browser and return to Visual Studio.</span></span> <span data-ttu-id="d6f2f-192">請注意您已建立整個 CRUD 員 實體的整個來源來檢視模型-應用程式而不需要撰寫一行程式碼 ！</span><span class="sxs-lookup"><span data-stu-id="d6f2f-192">Notice that you have created the whole CRUD for the person entity throughout your application -from the model to the views- without having to write a single line of code!</span></span>

<a id="Ex1Task3"></a>

<a id="Task_3-_Updating_the_database_using_Entity_Framework_Migrations"></a>
#### <a name="task-3--updating-the-database-using-entity-framework-migrations"></a><span data-ttu-id="d6f2f-193">工作 3-更新使用 Entity Framework 移轉資料庫</span><span class="sxs-lookup"><span data-stu-id="d6f2f-193">Task 3- Updating the database using Entity Framework Migrations</span></span>

<span data-ttu-id="d6f2f-194">在這項工作中，您將更新使用 Entity Framework 移轉的資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-194">In this task you will update the database using Entity Framework Migrations.</span></span> <span data-ttu-id="d6f2f-195">您會發現若要變更模型，並使用 Entity Framework 的移轉功能，以反映您的資料庫中的變更是多麼的輕鬆。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-195">You will discover how easy it is to change the model and reflect the changes in your databases by using the Entity Framework Migrations feature.</span></span>

1. <span data-ttu-id="d6f2f-196">開啟 封裝管理員主控台。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-196">Open the Package Manager Console.</span></span> <span data-ttu-id="d6f2f-197">選取**工具 |程式庫套件管理員 |Package Manager Console**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-197">Select **Tools | Library Package Manager | Package Manager Console**.</span></span>
2. <span data-ttu-id="d6f2f-198">在 Package Manager Console 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-198">In the Package Manager Console, enter the following command:</span></span>

    <span data-ttu-id="d6f2f-199">PMC</span><span class="sxs-lookup"><span data-stu-id="d6f2f-199">PMC</span></span>

    [!code-powershell[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample2.ps1)]

    <span data-ttu-id="d6f2f-200">![啟用移轉](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image11.png "啟用移轉")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-200">![Enabling Migrations](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image11.png "Enabling Migrations")</span></span>

    <span data-ttu-id="d6f2f-201">*啟用移轉*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-201">*Enabling migrations*</span></span>

    <span data-ttu-id="d6f2f-202">啟用移轉命令會建立**移轉**資料夾，其中包含指令碼來初始化資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-202">The Enable-Migration command creates the **Migrations** folder, which contains a script to initialize the database.</span></span>

    <span data-ttu-id="d6f2f-203">![Migrations 資料夾](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image12.png "Migrations 資料夾")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-203">![Migrations folder](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image12.png "Migrations folder")</span></span>

    <span data-ttu-id="d6f2f-204">*Migrations 資料夾*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-204">*Migrations folder*</span></span>
3. <span data-ttu-id="d6f2f-205">開啟**configuration.cs 中**Migrations 資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-205">Open the **Configuration.cs** file in the Migrations folder.</span></span> <span data-ttu-id="d6f2f-206">尋找類別建構函式並將變更**AutomaticMigrationsEnabled**值設定為*true*。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-206">Locate the class constructor and change the **AutomaticMigrationsEnabled** value to *true*.</span></span>


    [!code-csharp[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample3.cs)]
4. <span data-ttu-id="d6f2f-207">開啟 Person 類別並加入個人的中間名的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-207">Open the Person class and add an attribute for the person's middle name.</span></span> <span data-ttu-id="d6f2f-208">利用此新屬性，您要變更模型。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-208">With this new attribute, you are changing the model.</span></span>


    [!code-csharp[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample4.cs)]
5. <span data-ttu-id="d6f2f-209">選取**建置 |建置方案**上建置應用程式的功能表。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-209">Select **Build | Build Solution** on the menu to build the application.</span></span>

    <span data-ttu-id="d6f2f-210">![建置應用程式](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image13.png "建置應用程式")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-210">![Building the application](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image13.png "Building the application")</span></span>

    <span data-ttu-id="d6f2f-211">*建置應用程式*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-211">*Building the application*</span></span>
6. <span data-ttu-id="d6f2f-212">在 Package Manager Console 中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-212">In the Package Manager Console, enter the following command:</span></span>

    <span data-ttu-id="d6f2f-213">PMC</span><span class="sxs-lookup"><span data-stu-id="d6f2f-213">PMC</span></span>

    [!code-powershell[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample5.ps1)]

    <span data-ttu-id="d6f2f-214">此命令會尋找資料物件中的變更，然後，它會在其中加入必要的命令，據此修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-214">This command will look for changes in the data objects, and then, it will add the necessary commands to modify the database accordingly.</span></span>

    <span data-ttu-id="d6f2f-215">![加入 「 中間名](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image14.png "加入中間名")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-215">![Adding a middle name](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image14.png "Adding a middle name")</span></span>

    <span data-ttu-id="d6f2f-216">*加入 「 中間名*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-216">*Adding a middle name*</span></span>
7. <span data-ttu-id="d6f2f-217">（選擇性）您可以執行下列命令來產生 SQL 指令碼有差異的更新。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-217">(Optional) You can run the following command to generate a SQL script with the differential update.</span></span> <span data-ttu-id="d6f2f-218">這可讓您手動更新資料庫 （在此情況下有不必要），或適用於其他資料庫中的變更：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-218">This will let you update the database manually (In this case it's not necessary), or apply the changes in other databases:</span></span>

    <span data-ttu-id="d6f2f-219">PMC</span><span class="sxs-lookup"><span data-stu-id="d6f2f-219">PMC</span></span>

    [!code-powershell[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample6.ps1)]

    <span data-ttu-id="d6f2f-220">![產生 SQL 指令碼](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image15.png "產生 SQL 指令碼")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-220">![Generating a SQL script](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image15.png "Generating a SQL script")</span></span>

    <span data-ttu-id="d6f2f-221">*產生 SQL 指令碼*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-221">*Generating a SQL script*</span></span>

    <span data-ttu-id="d6f2f-222">![SQL 指令碼更新](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image16.png "SQL 指令碼更新")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-222">![SQL Script update](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image16.png "SQL Script update")</span></span>

    <span data-ttu-id="d6f2f-223">*SQL 指令碼更新*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-223">*SQL Script update*</span></span>
8. <span data-ttu-id="d6f2f-224">在 Package Manager Console 中，輸入下列命令以更新資料庫：</span><span class="sxs-lookup"><span data-stu-id="d6f2f-224">In the Package Manager Console, enter the following command to update the database:</span></span>

    <span data-ttu-id="d6f2f-225">PMC</span><span class="sxs-lookup"><span data-stu-id="d6f2f-225">PMC</span></span>

    [!code-powershell[Main](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/samples/sample7.ps1)]

    <span data-ttu-id="d6f2f-226">![更新資料庫](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image17.png "更新資料庫")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-226">![Updating the Database](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image17.png "Updating the Database")</span></span>

    <span data-ttu-id="d6f2f-227">*更新資料庫*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-227">*Updating the Database*</span></span>

    <span data-ttu-id="d6f2f-228">這會新增**MiddleName**中的資料行**人員**表格以比對目前的定義**人員**類別。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-228">This will add the **MiddleName** column in the **People** table to match the current definition of the **Person** class.</span></span>
9. <span data-ttu-id="d6f2f-229">資料庫的更新，以滑鼠右鍵按一下 [控制器] 資料夾，並選取**新增 |控制器**加入人員控制器再次 （完成相同的值）。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-229">Once the database is updated, right-click the Controller folder and select **Add | Controller** to add the Person controller again (Complete with the same values).</span></span> <span data-ttu-id="d6f2f-230">這會更新現有的方法和檢視表加入新的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-230">This will update the existing methods and views adding the new attribute.</span></span>

    <span data-ttu-id="d6f2f-231">![加入控制器更新](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image18.png "加入控制器更新")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-231">![Adding a controller update](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image18.png "Adding a controller update")</span></span>

    <span data-ttu-id="d6f2f-232">*更新控制器*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-232">*Updating the controller*</span></span>
10. <span data-ttu-id="d6f2f-233">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-233">Click **Add**.</span></span> <span data-ttu-id="d6f2f-234">然後，選取 值**覆寫 PersonController.cs**和**覆寫相關聯的檢視**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-234">Then, select the values **Overwrite PersonController.cs** and the **Overwrite associated views** and click **OK**.</span></span>

    ![加入控制器覆寫](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image19.png)

    <span data-ttu-id="d6f2f-236">*更新控制器*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-236">*Updating the controller*</span></span>

<a id="Ex1Task4"></a>

<a id="Task4-_Running_the_application"></a>
#### <a name="task4--running-the-application"></a><span data-ttu-id="d6f2f-237">Task4-執行應用程式</span><span class="sxs-lookup"><span data-stu-id="d6f2f-237">Task4- Running the application</span></span>

1. <span data-ttu-id="d6f2f-238">按 **F5** 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-238">Press **F5** to run the application.</span></span>
2. <span data-ttu-id="d6f2f-239">開啟**/Person**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-239">Open **/Person**.</span></span> <span data-ttu-id="d6f2f-240">請注意，已保留資料，而中間名資料行已加入。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-240">Notice that the data was preserved, while the middle name column was added.</span></span>

    <span data-ttu-id="d6f2f-241">![加入的中間名](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image20.png "加入的中間名")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-241">![Middle Name added](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image20.png "Middle Name added")</span></span>

    <span data-ttu-id="d6f2f-242">*加入的中間名*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-242">*Middle Name added*</span></span>
3. <span data-ttu-id="d6f2f-243">如果您按一下**編輯**，您將能夠加入至目前的人員的中間名。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-243">If you click **Edit**, you will be able to add a middle name to the current person.</span></span>

    <span data-ttu-id="d6f2f-244">![中間名 edition](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image21.png "中間名版本")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-244">![Middle Name edition](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image21.png "Middle Name edition")</span></span>

* * *

<a id="Summary"></a>

<a id="Summary"></a>
## <a name="summary"></a><span data-ttu-id="d6f2f-245">總結</span><span class="sxs-lookup"><span data-stu-id="d6f2f-245">Summary</span></span>

<span data-ttu-id="d6f2f-246">在這個實際操作實驗室中，您已經學會簡單的步驟來建立 ASP.NET MVC 4 Scaffolding 使用任何模型類別 CRUD 作業。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-246">In this Hands-On lab, you have learned simple steps to create CRUD operations with ASP.NET MVC 4 Scaffolding using any model class.</span></span> <span data-ttu-id="d6f2f-247">然後，您已經學會如何使用 Entity Framework 移轉您的應用程式層來檢視資料庫-執行的端對端的更新。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-247">Then, you have learned how to perform an end to end update in your application -from the database to the views- by using Entity Framework Migrations.</span></span>

<a id="AppendixA"></a>

<a id="Appendix_A_Installing_Visual_Studio_Express_2012_for_Web"></a>
## <a name="appendix-a-installing-visual-studio-express-2012-for-web"></a><span data-ttu-id="d6f2f-248">附錄 a： 安裝 Visual Studio Express 2012 for Web</span><span class="sxs-lookup"><span data-stu-id="d6f2f-248">Appendix A: Installing Visual Studio Express 2012 for Web</span></span>

<span data-ttu-id="d6f2f-249">您可以安裝**Microsoft Visual Studio Express 2012 for Web**或另一個&quot;Express&quot;版本使用 **[Microsoft Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)** .</span><span class="sxs-lookup"><span data-stu-id="d6f2f-249">You can install **Microsoft Visual Studio Express 2012 for Web** or another &quot;Express&quot; version using the **[Microsoft Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)**.</span></span> <span data-ttu-id="d6f2f-250">下列指示將引導您逐步完成安裝所需*Visual studio Express 2012 for Web*使用*Microsoft Web Platform Installer*。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-250">The following instructions guide you through the steps required to install *Visual studio Express 2012 for Web* using *Microsoft Web Platform Installer*.</span></span>

1. <span data-ttu-id="d6f2f-251">移至[ [https://go.microsoft.com/? linkid = 9810169](https://go.microsoft.com/?linkid=9810169)](https://go.microsoft.com/?linkid=9810169)。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-251">Go to [[https://go.microsoft.com/? linkid=9810169](https://go.microsoft.com/?linkid=9810169)](https://go.microsoft.com/?linkid=9810169).</span></span> <span data-ttu-id="d6f2f-252">或者，如果您已安裝 Web Platform Installer，您可以開啟它，並搜尋產品&quot; *Visual Studio Express 2012 for Web 與 Windows Azure SDK*&quot;。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-252">Alternatively, if you already have installed Web Platform Installer, you can open it and search for the product &quot;*Visual Studio Express 2012 for Web with Windows Azure SDK*&quot;.</span></span>
2. <span data-ttu-id="d6f2f-253">按一下**立即安裝**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-253">Click on **Install Now**.</span></span> <span data-ttu-id="d6f2f-254">如果您不需要**Web Platform Installer**您會重新導向至下載並安裝第一次。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-254">If you do not have **Web Platform Installer** you will be redirected to download and install it first.</span></span>
3. <span data-ttu-id="d6f2f-255">一次**Web Platform Installer**開啟時，按一下 **安裝**，啟動安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-255">Once **Web Platform Installer** is open, click **Install** to start the setup.</span></span>

    <span data-ttu-id="d6f2f-256">![安裝 Visual Studio Express](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image22.png "安裝 Visual Studio Express")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-256">![Install Visual Studio Express](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image22.png "Install Visual Studio Express")</span></span>

    <span data-ttu-id="d6f2f-257">*安裝 Visual Studio Express*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-257">*Install Visual Studio Express*</span></span>
4. <span data-ttu-id="d6f2f-258">閱讀所有產品的授權和詞彙，然後按一下**我接受**才能繼續。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-258">Read all the products' licenses and terms and click **I Accept** to continue.</span></span>

    ![接受授權條款](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image23.png)

    <span data-ttu-id="d6f2f-260">*接受授權條款*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-260">*Accepting the license terms*</span></span>
5. <span data-ttu-id="d6f2f-261">等待直到完成下載和安裝程序。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-261">Wait until the downloading and installation process completes.</span></span>

    ![安裝進度](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image24.png)

    <span data-ttu-id="d6f2f-263">*安裝進度*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-263">*Installation progress*</span></span>
6. <span data-ttu-id="d6f2f-264">當安裝完成時，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-264">When the installation completes, click **Finish**.</span></span>

    ![安裝已完成](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image25.png)

    <span data-ttu-id="d6f2f-266">*安裝已完成*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-266">*Installation completed*</span></span>
7. <span data-ttu-id="d6f2f-267">按一下**結束**關閉 Web Platform Installer。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-267">Click **Exit** to close Web Platform Installer.</span></span>
8. <span data-ttu-id="d6f2f-268">若要開啟 Visual Studio Express for Web，請移至**啟動**畫面上，並開始書寫&quot; **VS Express**&quot;，然後按一下  **VS Express for Web**並排顯示。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-268">To open Visual Studio Express for Web, go to the **Start** screen and start writing &quot;**VS Express**&quot;, then click on the **VS Express for Web** tile.</span></span>

    ![VS Express for Web 方塊](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image26.png)

    <span data-ttu-id="d6f2f-270">*VS Express for Web 方塊*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-270">*VS Express for Web tile*</span></span>

<a id="AppendixB"></a>

<a id="Appendix_B_Using_Code_Snippets"></a>
## <a name="appendix-b-using-code-snippets"></a><span data-ttu-id="d6f2f-271">附錄 b： 使用程式碼片段</span><span class="sxs-lookup"><span data-stu-id="d6f2f-271">Appendix B: Using Code Snippets</span></span>

<span data-ttu-id="d6f2f-272">程式碼片段，您會有您需要在您可以的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-272">With code snippets, you have all the code you need at your fingertips.</span></span> <span data-ttu-id="d6f2f-273">實驗室文件會告訴您完全時您可以使用它們，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-273">The lab document will tell you exactly when you can use them, as shown in the following figure.</span></span>

<span data-ttu-id="d6f2f-274">![若要將程式碼插入您的專案中使用 Visual Studio 程式碼片段](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image27.png "使用 Visual Studio 程式碼片段，將程式碼插入您的專案")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-274">![Using Visual Studio code snippets to insert code into your project](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image27.png "Using Visual Studio code snippets to insert code into your project")</span></span>

<span data-ttu-id="d6f2f-275">*若要將程式碼插入您的專案中使用 Visual Studio 程式碼片段*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-275">*Using Visual Studio code snippets to insert code into your project*</span></span>

<span data-ttu-id="d6f2f-276">***若要加入的程式碼片段，使用鍵盤 （僅限 C#)***</span><span class="sxs-lookup"><span data-stu-id="d6f2f-276">***To add a code snippet using the keyboard (C# only)***</span></span>

1. <span data-ttu-id="d6f2f-277">將游標放在您想要插入的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-277">Place the cursor where you would like to insert the code.</span></span>
2. <span data-ttu-id="d6f2f-278">開始鍵入片段名稱 （不含空格或連字號）。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-278">Start typing the snippet name (without spaces or hyphens).</span></span>
3. <span data-ttu-id="d6f2f-279">觀察 IntelliSense 會顯示比對程式碼片段的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-279">Watch as IntelliSense displays matching snippets' names.</span></span>
4. <span data-ttu-id="d6f2f-280">選取正確的程式碼片段 （或直到選取整個程式碼片段名稱時，保留 輸入）。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-280">Select the correct snippet (or keep typing until the entire snippet's name is selected).</span></span>
5. <span data-ttu-id="d6f2f-281">按下 Tab 鍵兩次的游標位置插入程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-281">Press the Tab key twice to insert the snippet at the cursor location.</span></span>

<span data-ttu-id="d6f2f-282">![開始輸入程式碼片段名稱](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image28.png "開始鍵入片段名稱")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-282">![Start typing the snippet name](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image28.png "Start typing the snippet name")</span></span>

<span data-ttu-id="d6f2f-283">*開始輸入程式碼片段名稱*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-283">*Start typing the snippet name*</span></span>

<span data-ttu-id="d6f2f-284">![按 Tab 鍵選取反白顯示的程式碼片段](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image29.png "按 Tab 鍵以選取反白顯示的程式碼片段")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-284">![Press Tab to select the highlighted snippet](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image29.png "Press Tab to select the highlighted snippet")</span></span>

<span data-ttu-id="d6f2f-285">*按 Tab 鍵選取反白顯示的程式碼片段*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-285">*Press Tab to select the highlighted snippet*</span></span>

<span data-ttu-id="d6f2f-286">![按 Tab 鍵一次程式碼片段就會擴展](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image30.png "按 Tab 鍵一次程式碼片段就會擴展")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-286">![Press Tab again and the snippet will expand](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image30.png "Press Tab again and the snippet will expand")</span></span>

<span data-ttu-id="d6f2f-287">*按 Tab 鍵一次程式碼片段就會擴展*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-287">*Press Tab again and the snippet will expand*</span></span>

<span data-ttu-id="d6f2f-288">***若要加入的程式碼片段，使用滑鼠 （C#、 Visual Basic 和 XML）*** 1。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-288">***To add a code snippet using the mouse (C#, Visual Basic and XML)*** 1.</span></span> <span data-ttu-id="d6f2f-289">以滑鼠右鍵按一下您要插入程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-289">Right-click where you want to insert the code snippet.</span></span>

1. <span data-ttu-id="d6f2f-290">選取**插入程式碼片段**後面**我的程式碼片段**。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-290">Select **Insert Snippet** followed by **My Code Snippets**.</span></span>
2. <span data-ttu-id="d6f2f-291">透過在按一下挑選清單中，從相關的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="d6f2f-291">Pick the relevant snippet from the list, by clicking on it.</span></span>

<span data-ttu-id="d6f2f-292">![以滑鼠右鍵按一下您要插入程式碼片段，然後選取 插入程式碼片段](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image31.png "以滑鼠右鍵按一下您要插入程式碼片段，然後選取 插入程式碼片段")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-292">![Right-click where you want to insert the code snippet and select Insert Snippet](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image31.png "Right-click where you want to insert the code snippet and select Insert Snippet")</span></span>

<span data-ttu-id="d6f2f-293">*以滑鼠右鍵按一下您要插入程式碼片段，然後選取 插入程式碼片段*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-293">*Right-click where you want to insert the code snippet and select Insert Snippet*</span></span>

<span data-ttu-id="d6f2f-294">![透過在按一下挑選清單中，從相關的程式碼片段](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image32.png "上它即可挑選清單中，從相關的程式碼片段")</span><span class="sxs-lookup"><span data-stu-id="d6f2f-294">![Pick the relevant snippet from the list, by clicking on it](aspnet-mvc-4-entity-framework-scaffolding-and-migrations/_static/image32.png "Pick the relevant snippet from the list, by clicking on it")</span></span>

<span data-ttu-id="d6f2f-295">*透過在按一下挑選清單中，從相關的程式碼片段*</span><span class="sxs-lookup"><span data-stu-id="d6f2f-295">*Pick the relevant snippet from the list, by clicking on it*</span></span>