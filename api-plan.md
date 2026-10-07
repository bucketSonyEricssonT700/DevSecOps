 api-plan.md
Реализовать в эпиай:
список заявок, который содержит в себе поля: id, содержания заявки, даты составления заявки, приоритета заявки 


var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();


var requests = new List<Request>
{
    new Request(1, "Собака умерла", "15:05", 7),
    new Request(2, "Я умер", 1)
};

app.MapGet("/", () => "Hello World");

app.MapGet("/hello/{name}/", (string name) =>
{
    var hello = new
    {
        Message = $"Hello, {name}!",
        Status = "Success"
    };
    return Results.Ok(hello);
});

app.Run();

public record Request(int Id, string text, string created, byte priority);
