[[Programmering]]



**Entity Framework**
I DBContext
public DiveDeepContext(DbContextOptions dbContextOptions) : base(dbContextOptions)
{

}

protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    base.OnModelCreating(modelBuilder);

		eksempel:
		 modelBuilder.Entity<Booking>().HasOne<User>(r => r.User).WithMany(b => b.Bookings)
     .HasForeignKey(b => b.UserId);
}

Seeded data:
modelBuilder.Entity<FinAvailableSize>().HasData(
    new FinAvailableSize { FinId = 27, FinSize = Size.XS },
    new FinAvailableSize { FinId = 27, FinSize = Size.S },


**Identity**

i Program.cs
builder.Services.AddDefaultIdentity<User>(options => options.SignIn.RequireConfirmedAccount = false)
    .AddRoles<IdentityRole>()
    .AddEntityFrameworkStores<DiveDeepContext>();

Tilføj Scaffolding for Login service



Add-migration xxxx
update-database
drop-database
