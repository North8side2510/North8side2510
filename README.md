- 👋 Hi, I’m @North8side2510
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
North8side2510/North8side2510 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
# Adding swagger documentation

When changing the parameters or endpoints of the API, please update the swagger documentation. 

1. Visit the open source [editor](https://editor.swagger.io/)
2. Copy and paste the swagger from [swagger.json](./swagger.json) in the `docs` folder
3. The editor will ask you to transform the file into yaml, click yes
4. Make your changes and make sure the swagger is valid. The editor when if it is not
5. Click on `File`, then `Convert and save as json` and update the [swagger.json](./swagger.json) fileprotected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.Entity<Blog>()
        .ToTable(tb => tb.HasTrigger("SomeTrigger"));
}public class BlankTriggerAddingConvention : IModelFinalizingConvention
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
}<ItemGroup>
  <ProjectReference Include="..\WebApplication1.Migrations\WebApplication1.Migrations.csproj" />
</ItemGroup>services.AddDbContext<ApplicationDbContext>(
    options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection"),
            x => x.MigrationsAssembly("WebApplication1.Migrations")));
