I'mI'mecho "# 256root" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/North8side2510/256root.git
git push -u origin main# Adding swagger documentation

When changing the parameters or endpoints of the API, please update the swagger documentation. 

1. Visit the open source [editor](https://editor.swagger.io/)
2. Copy and paste the swagger from [swagger.json](./swagger.json) in the `docs` folder
3. The editor will ask you to transform the file into yaml, click yes
4. Make your changes and make sure the swagger is valid. The editor when if it is not
5. Click on `File`, then `Convert and save as json` and update the [swagger.json](./swagger.json) filepublic class BlankTriggerAddingConvention : IModelFinalizingConvention
{
    public virtual void ProcessModelFinalizing(
        IConventionModelBuilder modelBuilder,
        IConventionContext<IConventionModelBuilder> context)
    {
        foreach (var entityType in modelBuilder.Metadata.GetEntityTypes())
        {
            var table = StoreObjectIdentifier.Create(entityType, StoreObjectType.Table);
            if (table != null
                && entityType.GetDeclaredTriggers().All(t => t.GetDatabaseName(table.Value) == null)
                && (entityType.BaseType == null
                    || entityType.GetMappingStrategy() != RelationalAnnotationNames.TphMappingStrategy))
            {
                entityType.Builder.HasTrigger(table.Value.Name + "_Trigger");
            }

            foreach (var fragment in entityType.GetMappingFragments(StoreObjectType.Table))
            {
                if (entityType.GetDeclaredTriggers().All(t => t.GetDatabaseName(fragment.StoreObject) == null))
                {
                    entityType.Builder.HasTrigger(fragment.StoreObject.Name + "_Trigger");
                }
            }
        }
    }
}services.AddDbContext<ApplicationDbContext>(
    options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection"),
            x => x.MigrationsAssembly("WebApplication1.Migrations")));
   Overview <self>
   basics/install
   basics/quickstart
title: 'Lesson 24: Styling the skip link'work-item.htmla4a85f6477dfd49d36b1d4a3fd1f0762f5658148
af90e4d5a110dcf6e1929a510898c2ad28c45eec
hero.image item.summary item.secondary
item.primary
item.title
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="string"
          android:sharedUserId="string"
          android:sharedUserLabel="string resource" 
          android:sharedUserMaxSdkVersion="integer"
          android:versionCode="integer"
          android:versionName="string"
          android:installLocation=["auto" | "internalOnly" | "preferExternal"] >
    ...# Required metadata
sonar.projectKey=java-sonar-runner-simple
sonar.projectName=Simple Java project analyzed with the SonarQube Runner
sonar.projectVersion=1.0

# Comma-separated paths to directories with sources (required)
sonar.sources=src

# Language
sonar.language=java

# Encoding of the source files
sonar.sourceEncoding=UTF-8
</manifest>

});f5f5dc
