# Profile-
my profile 
use actix_web::{get, App, HttpResponse, HttpServer, Responder};

#[get("/")]
async fn about() -> impl Responder {
    let html = r#"
    <!DOCTYPE html>
    <html>
    <head>
        <title>About Me - Taylor Harding</title>
        <style>
            body {
                font-family: -apple-system, BlinkMacSystemFont, sans-serif;
                background: #0b0f19;
                color: #e6edf3;
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100vh;
                margin: 0;
            }
            .card {
                background: #111827;
                padding: 2rem;
                border-radius: 16px;
                max-width: 650px;
                box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            }
            h1 {
                color: #60a5fa;
                margin-bottom: 0.5rem;
            }
            h2 {
                color: #9ca3af;
                font-weight: normal;
                margin-top: 0;
            }
            p {
                line-height: 1.6;
            }
            .highlight {
                color: #34d399;
            }
            a {
                color: #22c55e;
                text-decoration: none;
            }
        </style>
    </head>
    <body>
        <div class="card">
            <h1>Taylor Harding 👋</h1>
            <h2>Web3 Recruitment | Odiin</h2>

            <p>
                I specialize in connecting top-tier talent with cutting-edge companies
                in the <span class="highlight">Web3, blockchain, and crypto</span> space.
            </p>

            <p>
                At <span class="highlight">Odiin</span>, I work with innovative teams building
                the future of decentralized technology — from infrastructure and protocols
                to DeFi and next-gen applications.
            </p>

            <p>
                Passionate about people, technology, and the evolution of the internet,
                I focus on helping companies scale with the right talent while supporting
                candidates in finding meaningful opportunities in Web3.
            </p>

            <p>
                🔗 <a href="https://www.linkedin.com/in/taylor-harding-48569769/" target="_blank">
                Connect with me on LinkedIn
                </a>
            </p>
        </div>
    </body>
    </html>
    "#;

    HttpResponse::Ok()
        .content_type("text/html")
        .body(html)
}

#[actix_web::main]
async fn main() -> std::io::Result<()> {
    println!("Running at http://127.0.0.1:8080");

    HttpServer::new(|| {
        App::new()
            .service(about)
    })
    .bind(("127.0.0.1", 8080))?
    .run()
    .await
}
