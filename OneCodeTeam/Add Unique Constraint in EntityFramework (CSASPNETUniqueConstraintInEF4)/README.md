# Add Unique Constraint in EntityFramework (CSASPNETUniqueConstraintInEF4)
## Requires
- Visual Studio 2010
## License
- MS-LPL
## Technologies
- ASP.NET
## Topics
- ASP.NET
## Updated
- 12/10/2012
## Description

<h1>How to add Unique Constraint in EntityFramework (CSASPNETUniqueConstraintInEF4)</h1>
<h2>Introduction</h2>
<p class="MsoNormal">This project demonstrates how to add unique constraint in Entity Framework 4.3. Many customers need a Unique Attribute in EntityFramework4.3, but until now, there is no any published DLL or tool in Code-First of Entity Framework to serve
 this purpose.</p>
<h2>Building the Sample</h2>
<p class="MsoNormal">To install EntityFramework, run the following command in the
<b style="">Package Manager Console</b> </p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>PowerShell</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">powershell</span>

<pre id="codePreview" class="powershell">
PM&gt; Install-Package EntityFramework -Version 4.3.1

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<h2>Running the Sample</h2>
<p class="MsoListParagraphCxSpFirst" style=""><b style=""><span style=""><span style="">Step 1.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span></b>Open the CSASPNETUniqueConstraintInEF4.sln file. </p>
<p class="MsoListParagraphCxSpLast" style=""><b style=""><span style=""><span style="">Step 2.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span></b>Open the Program class to modify the Main method. Add two items to the &quot;Categories&quot; as below:</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
g.Categories.Add(new Category { Id = 1, Name = &quot;Category&quot; });
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; g.Categories.Add(new Category { Id = 2, IdentifyCode = 2, Name = &quot;Category&quot; });

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraphCxSpFirst" style=""><b style=""><span style=""><span style="">Step 3.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span></b><span style="">After that</span><span style="">, you can</span><span style=""> press &quot;Ctrl&#43;F5&quot; to run</span><span style=""> the sample</span><span style="">.<br>
</span><span style=""><img src="72358-image.png" alt="" width="576" height="292" align="middle">
</span></p>
<p class="MsoListParagraphCxSpMiddle" style=""><b style=""><span style=""><span style="">Step 4.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span></b>Remove the value of IdentifyCode and then run the Program again. You will encounter an error.</p>
<p class="MsoListParagraphCxSpLast" style=""><b style=""><span style=""><span style="">Step 5.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span></b>The validation is complete.</p>
<h2>Using the Code</h2>
<p class="MsoListParagraphCxSpFirst" style=""><span style=""><span style="">Step 1.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create a C# &quot;Console Application&quot; in Visual Studio 2010 and name it as &quot;CSASPNETUniqueConstraintInEF4.&quot;</p>
<p class="MsoListParagraphCxSpMiddle" style=""><span style=""><span style="">Step 2.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span><span style="">Add the assembly reference follow the steps below.<br>
<span style="">&nbsp;</span><span style="color:black">Project-&gt; References -&gt;…</span></span>
<span style="color:black">EntityFramework</span><span style="">.dll</span> </p>
<p class="MsoListParagraphCxSpLast" style=""><span style=""><span style="">Step 3.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create a custom attribute which is inherited from System.Attribute. It is used to specify a unique constraint to the corresponding field.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
///&lt;summary&gt;
&nbsp;&nbsp; ///A unique attribute
&nbsp;&nbsp; ///&lt;/summary&gt;
&nbsp;&nbsp; [AttributeUsage(AttributeTargets.Property, AllowMultiple = false, Inherited = true)]
&nbsp;&nbsp; public class UniqueKeyAttribute : Attribute
&nbsp;&nbsp; {
&nbsp;&nbsp; }

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraph" style=""><span style=""><span style="">Step 4.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create a Database Generator by implementing the IDatabaseInitializer interface. In the class we will try to analyze the Model Entity by reflecting them one by one and fetch the properties with &quot;unique&quot; attribute and then call
 SQL statement to create database.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
/// &lt;summary&gt;
&nbsp;&nbsp; ///&nbsp; Try to analyze the ModelEntity by reflecting them one by one and then
&nbsp;&nbsp; ///&nbsp; fetch the properties with &quot;unique&quot; attribute and then do calling Sql statement to create database.
&nbsp;&nbsp; /// &lt;/summary&gt;
&nbsp;&nbsp; /// &lt;typeparam name=&quot;T&quot;&gt;&lt;/typeparam&gt;
&nbsp;&nbsp; public class MyDbGenerator&lt;T&gt; : IDatabaseInitializer&lt;T&gt; where T : DbContext
&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public void InitializeDatabase(T context)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; context.Database.Delete();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; context.Database.Create();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//Fetch all the father class's public properties
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; var fatherPropertyNames = typeof(DbContext).GetProperties().Select(pi =&gt; pi.Name).ToList();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //Loop each dbset's T
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; foreach (PropertyInfo item in typeof(T).GetProperties().Where(p =&gt; fatherPropertyNames.IndexOf(p.Name) &lt; 0).Select(p =&gt; p))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //fetch the type of &quot;T&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Type entityModelType = item.PropertyType.GetGenericArguments()[0];
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; var allfieldNames = from prop in entityModelType.GetProperties()
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; where prop.GetCustomAttributes(typeof(UniqueKeyAttribute), true).Count() &gt; 0
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; select prop.Name;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; foreach (string s in allfieldNames)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;{
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; context.Database.ExecuteSqlCommand(&quot;alter table &quot; &#43; entityModelType.Name &#43; &quot; add unique(&quot; &#43; s &#43; &quot;)&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp; }

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraph" style=""><span style=""><span style="">Step 5.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create a model entity. Add the custom attribute to the IdentifyCode field.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
/// &lt;summary&gt;
&nbsp;&nbsp;&nbsp; /// Category Class
&nbsp;&nbsp;&nbsp; /// &lt;/summary&gt;
&nbsp;&nbsp;&nbsp; public class Category
&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Key]
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public int Id { get; set; }
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [UniqueKey] // Unique Key
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public int IdentifyCode { get; set; }
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public string Name { get; set; }
&nbsp;&nbsp;&nbsp; }

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraph" style=""><span style=""><span style="">Step 6.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create a class inherited from DbContext.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
public class DbG : DbContext
&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /// &lt;summary&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /// This method is called when the model for a derived context has been initialized, but 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// before the model has been locked down and used to initialize the context. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/// &lt;/summary&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /// &lt;param name=&quot;modelBuilder&quot;&gt;It is used to map CLR classes to a database schema. &lt;/param&gt;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; protected override void OnModelCreating(DbModelBuilder modelBuilder)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //&nbsp; Disable the default PluralizingTableNameConvention
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; modelBuilder.Conventions.Remove&lt;PluralizingTableNameConvention&gt;();
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public DbSet&lt;Category&gt; Categories { get; set; }
&nbsp;&nbsp;&nbsp; }



</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraph" style=""><span style=""><span style="">Step 7.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Create Database instance and DbContext instance and then add some model instance to DbSet. Save the changes.</p>
<div class="scriptcode">
<div class="pluginEditHolder" pluginCommand="mceScriptCode">
<div class="title"><span>C#</span></div>
<div class="pluginLinkHolder"><span class="pluginEditHolderLink">Edit</span>|<span class="pluginRemoveHolderLink">Remove</span>
</div>
<span class="hidden">csharp</span>

<pre id="codePreview" class="csharp">
static void Main(string[] args)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Gets or sets the database initialization strategy.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Database.SetInitializer&lt;DbG&gt;(new MyDbGenerator&lt;DbG&gt;());


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; using (DbG g = new DbG())
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;g.Categories.Add(new Category { Id = 1, Name = &quot;Category&quot; });
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; g.Categories.Add(new Category { Id = 2, IdentifyCode = 2, Name = &quot;Category&quot; });
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // saves all changes
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; g.SaveChanges();


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Console.WriteLine(&quot;OK&quot;);
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }

</pre>
</div>
</div>
<div class="endscriptcode">&nbsp;</div>
<p class="MsoListParagraph" style=""><span style=""><span style="">Step 8.<span style="font:7.0pt &quot;Times New Roman&quot;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span></span>Build and debug it.</p>
<h2>More Information</h2>
<p class="MsoNormal">Attribute Class<br>
<a href="http://msdn.microsoft.com/en-us/library/System.Attribute(v=vs.100).aspx">http://msdn.microsoft.com/en-us/library/System.Attribute(v=vs.100).aspx</a><br>
<span class="SpellE">DbContext</span> Class<br>
<a href="http://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext(v=VS.103).aspx">http://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext(v=VS.103).aspx</a><br>
<span class="SpellE">IDatabaseInitializer</span>&lt;<span class="SpellE">TContext</span>&gt; Interface<br>
<a href="http://msdn.microsoft.com/en-us/library/gg696323(v=VS.100).aspx">http://msdn.microsoft.com/en-us/library/gg696323(v=VS.100).aspx</a><br>
<span class="SpellE">PropertyInfo</span> Class<br>
<a href="http://msdn.microsoft.com/en-us/library/System.Reflection.PropertyInfo.aspx">http://msdn.microsoft.com/en-us/library/System.Reflection.PropertyInfo.aspx</a><br>
<span class="SpellE">Database.ExecuteSqlCommand</span> Method<br>
<a href="http://msdn.microsoft.com/en-us/library/system.data.entity.database.executesqlcommand%28v=VS.103%29.aspx">http://msdn.microsoft.com/en-us/library/system.data.entity.database.executesqlcommand%28v=VS.103%29.aspx</a><br>
<span class="SpellE">DbContext.OnModelCreating</span> Method<br>
<a href="http://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext.onmodelcreating(v=vs.103).aspx">http://msdn.microsoft.com/en-us/library/system.data.entity.dbcontext.onmodelcreating(v=vs.103).aspx</a><br>
<span class="SpellE">Database.SetInitializer</span>&lt;<span class="SpellE">TContext</span>&gt; Method<br>
<a href="http://msdn.microsoft.com/en-us/library/gg679461(v=VS.103).aspx">http://msdn.microsoft.com/en-us/library/gg679461(v=VS.103).aspx</a></p>
<hr>
<div><a href="http://go.microsoft.com/?linkid=9759640" style="margin-top:3px"><img alt="" src="http://bit.ly/onecodelogo">
</a></div>
