# <a name="advanced-dsc-authoring-for-composition-and-collaboration"></a><span data-ttu-id="cdb9b-101">Расширенная разработка DSC для композиции и совместной работы</span><span class="sxs-lookup"><span data-stu-id="cdb9b-101">Advanced DSC Authoring for Composition and Collaboration</span></span>

<span data-ttu-id="cdb9b-102">В этой статье описываются типы подходов для объединения конфигураций и ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-102">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="cdb9b-103">Целью каждого сценария является уменьшение сложности в том случае, когда для достижения конечного состояния сервера развертывания лучше всего использовать несколько конфигураций.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-103">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="cdb9b-104">В качестве примера можно привести несколько команд, работающих над развертыванием сервера: владелец приложения, поддерживающий состояние приложения, и основная команда, выпускающая изменения для базовых конфигураций системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-104">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="cdb9b-105">Здесь описаны особенности каждого подхода, включая преимущества и риски.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-105">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Конвейер](images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="cdb9b-107">Типы методов совместной разработки</span><span class="sxs-lookup"><span data-stu-id="cdb9b-107">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="cdb9b-108">Для реализации этой концепции существует два решения, встроенных в локальный диспетчер конфигураций.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-108">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="cdb9b-109">Концепция</span><span class="sxs-lookup"><span data-stu-id="cdb9b-109">Concept</span></span> | <span data-ttu-id="cdb9b-110">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="cdb9b-110">Detailed Information</span></span>
|-|-
| <span data-ttu-id="cdb9b-111">Частичные конфигурации</span><span class="sxs-lookup"><span data-stu-id="cdb9b-111">Partial Configurations</span></span> | [<span data-ttu-id="cdb9b-112">Документация</span><span class="sxs-lookup"><span data-stu-id="cdb9b-112">Documentation</span></span>](partialconfigs.md)
| <span data-ttu-id="cdb9b-113">Составные ресурсы</span><span class="sxs-lookup"><span data-stu-id="cdb9b-113">Composite Resources</span></span> | [<span data-ttu-id="cdb9b-114">Документация</span><span class="sxs-lookup"><span data-stu-id="cdb9b-114">Documentation</span></span>](authoringresourcecomposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="cdb9b-115">Понимание влияния каждого подхода</span><span class="sxs-lookup"><span data-stu-id="cdb9b-115">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="cdb9b-116">Любое из этих решений можно использовать для управления результатом развертывания сервера.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-116">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="cdb9b-117">Однако существует значительная разница, касающаяся влияния каждого подхода.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-117">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="cdb9b-118">Частичные конфигурации</span><span class="sxs-lookup"><span data-stu-id="cdb9b-118">Partial Configurations</span></span>

<span data-ttu-id="cdb9b-119">При использовании частичных конфигураций локальный диспетчер конфигураций настраивается для управления несколькими конфигурациями независимо друг от друга.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-119">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="cdb9b-120">Конфигурации компилируются независимо друг от друга и затем назначаются узлу.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-120">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="cdb9b-121">Для этого необходимо заранее настроить LCM с именем каждой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-121">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](images/PartialConfiguration.jpg)

<span data-ttu-id="cdb9b-123">Частичные конфигурации предоставляют двум или более командам полный контроль над конфигурацией сервера (часто без преимуществ взаимодействия или совместной работы).</span><span class="sxs-lookup"><span data-stu-id="cdb9b-123">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="cdb9b-124">Клиенты сообщили, что это может привести к конфликтам ресурсов, непреднамеренным переопределениям и, в конечном счете, потере реального контроля над конфигурацией ресурса.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-124">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="cdb9b-125">Кроме того, клиенты отметили, что в этой модели изменения конфигураций, находящихся под контролем команд, вряд ли пройдут полное тестирование в рамках конвейера выпуска, что приведет к непредвиденным результатам в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-125">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="cdb9b-126">**Крайне важно, чтобы для оценки всех выпусков изменений для серверов использовался один конвейер.**</span><span class="sxs-lookup"><span data-stu-id="cdb9b-126">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="cdb9b-127">На рисунке ниже команда Б выпускает частичную конфигурацию и передает ее команде А. Команда А выполняет свои тесты на сервере с обеими примененными конфигурациями.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-127">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="cdb9b-128">В этой модели только один центр имеет разрешение на внесение изменений в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-128">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](images/PartialSinglePipeline.jpg)

<span data-ttu-id="cdb9b-130">Если требуются изменения от команды Б, ее участники должны отправить запрос на вытягивание в среду управления версиями команды А.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-130">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="cdb9b-131">Затем команда А проверит изменения с помощью автоматизации тестирования и выпустит конфигурацию в производство, если будет уверена в том, что изменения не вызовут ошибок в приложениях или службах, размещенных на сервере.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-131">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="cdb9b-132">Составные ресурсы</span><span class="sxs-lookup"><span data-stu-id="cdb9b-132">Composite Resources</span></span>

<span data-ttu-id="cdb9b-133">Составной ресурс — это просто конфигурация DSC, упакованная в виде ресурса.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-133">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="cdb9b-134">Особых требований к настройке LCM для принятия составных ресурсов не существует.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-134">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="cdb9b-135">Ресурсы используются в новой конфигурации и в результатах одной процедуры компиляции в одном MOF-файле.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-135">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](images/CompositeResource.jpg)

<span data-ttu-id="cdb9b-137">Существует два распространенных сценария применения составных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-137">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="cdb9b-138">Первый — для снижения сложности и абстрагирования уникальных понятий.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-138">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="cdb9b-139">Второй — для упаковки базовых конфигураций, чтобы после прохождения всех тестов команда разработчиков приложений могла безопасно развертывать конфигурации в рабочей среде в рамках конвейера выпуска.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-139">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="cdb9b-140">Составные ресурсы повышают уровень композиции и совместной работы с помощью конвейера при одновременном формировании операционной готовности.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-140">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="cdb9b-141">Возможно, вы уже используете составные ресурсы, не осознавая этого.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-141">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="cdb9b-142">Примером является **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-142">An example is **ServiceSet**.</span></span>
<span data-ttu-id="cdb9b-143">Этот ресурс управляет состоянием нескольких служб Windows, не обращаясь к ним по отдельности.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-143">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="cdb9b-144">Свойство Name принимает массив строк для предоставления имени каждой службы.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-144">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="cdb9b-145">После компиляции конфигурации MOF-файл будет содержать уникальный раздел службы для каждого имени, переданного ServiceSet.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-145">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="cdb9b-146">Организации могут иметь агентов или промежуточное ПО, которое должно быть установлено на каждом сервере.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-146">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="cdb9b-147">Составной ресурс является лучшим вариантом для управления зависимостями, установкой и настройкой таких средств и служебных программ.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-147">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="cdb9b-148">Разработкой конфигурации в соответствии с требованиями занимается пользователь или команда, ответственные за решения для нескольких серверов.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-148">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="cdb9b-149">Затем конфигурация упаковывается в виде составного ресурса согласно инструкциям в документации по составным ресурсам.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-149">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="cdb9b-150">Наконец, новый составной ресурс следует опубликовать в расположение, например в общую папку или канал NuGet, где команды разработки приложений могут использовать его в своих конфигурациях.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-150">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="cdb9b-151">При каждом выпуске новой версии команда увеличивает номер версии в манифесте модуля для составного ресурса.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-151">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="cdb9b-152">Команды разработчиков приложений включают составной ресурс в конфигурацию, которую они создают для управления зависимостями приложения.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-152">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="cdb9b-153">При выпуске новой версии ресурса команды по эксплуатации и обеспечении безопасности уведомляют команды разработчиков приложений о новых изменениях.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-153">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="cdb9b-154">Команды разработчиков приложений могут запускать выпуск в рабочую среду, даже если единственным изменением является изменение базовых конфигураций.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-154">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="cdb9b-155">В этом случае существует возможность оценки влияния на приложения до возникновения риска сбоя службы.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-155">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="cdb9b-156">Примечание. В отзывах об использовании составных ресурсов содержатся критические замечания, указывающие на то, что при внесении изменений требуется скомпилировать и выпустить новый MOF-файл.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-156">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="cdb9b-157">Это сделано намеренно.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-157">This is by design.</span></span>
<span data-ttu-id="cdb9b-158">Каждый новый выпуск конфигурации должен содержать статическую ссылку на определенную версию каждого ресурса и должен быть протестирован перед развертыванием на узлах сервера в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-158">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="cdb9b-159">Процесс тестирования и выпуска изменений из системы управления версиями позволяет сформировать безопасную среду для выпуска изменений небольшими, но часто выходящими пакетами.</span><span class="sxs-lookup"><span data-stu-id="cdb9b-159">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="cdb9b-160">Дополнительные сведения об использовании конвейеров выпуска для управления базовой инфраструктурой см. в документе [Модель конвейера выпуска](http://aka.ms/thereleasepipelinemodel).</span><span class="sxs-lookup"><span data-stu-id="cdb9b-160">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodel).</span></span>