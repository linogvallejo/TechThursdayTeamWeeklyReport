# Tech Thursday - Team Weekly Status Application
## Instructions for migrating from SQL Server to MongoDB

1. Open Visual Studio 2022 and select the `TeamWeeklyStatusV2` solution.
2. Copy the MongoDB settings section below to the `appsettings.json` file located in:  
   `D:\source\repos\TeamWeeklyStatusV2\TeamWeeklyStatus.WebApi\`

   ```json
   "MongoDBSettings": {
       "ConnectionString": "mongodb+srv://linovallejo:Mi....0@cluster1.k4pfw.mongodb.net/",
       "DatabaseName": "team-weekly-status"
   }
   ```

3. Make sure a MongoDB-related Visual Studio project is placed in `D:\source\repos\MongoDB`.
4. Navigate to the Visual Studio Solution Explorer, right-click on the Solution, and then add the existing project `TeamWeeklyStatus.Infrastructure.MongoDB`.
5. Expand the MongoDB project and navigate to the **Dependencies > Projects** area. It's probable you will notice two projects with a caution icon. If this is the case, remove both, then re-add them. If there are no caution or warning icons, go to the following step.
6. Build the `TeamWeeklyStatus.Infrastructure.MongoDB` project to ensure that the newly introduced code is properly compiled.
7. Go to the `TeamWeeklyStatus.CompositionRoot` project and include `TeamWeeklyStatus.Infrastructure.MongoDB` project as a reference.
8. In the `TeamWeeklyStatus.CompositionRoot` project, navigate to the `DependencyInjection` class. Comment out the `using` statements for:

   ```csharp
   using TeamWeeklyStatus.Infrastructure;
   using Team.WeeklyStatus.Infrastructure.CompositionRoot;
   ```

9. Add the `using` statements for:

   ```csharp
   using TeamWeeklyStatus.Infrastructure.MongoDB;
   using TeamWeeklyStatus.Infrastructure.MongoDB.CompositionRoot;
   ```

Save the class file.

10. Clean and rebuild the Visual Studio solution.
11. Run the reloaded guy:
    1. Launch PowerShell and navigate to `D:\source\repos\TeamWeeklyStatusV2\team-weekly-status-front`.
    2. Run `npm run dev`.
    3. Launch `TeamWeeklyStatus.WebApi` in Debug mode from Visual Studio by clicking the `https` play button in the toolbar.
    4. Browse to [https://localhost:5173/](https://localhost:5173/).
    5. Enter `123` as the password for the `lgarcia@mangochango.com` user.
    6. Select the Team Weekly Status App Development team.



***

