import shutil

# Create the /docs/imgs folder
imgs_folder_path = "/mnt/data/portfolio_blog_demo/imgs"
os.makedirs(imgs_folder_path, exist_ok=True)

# Move the uploaded images to the /docs/imgs folder
image_files = [
    '/mnt/data/{9B4E157D-C9B4-4866-BF5A-E20AFBCB0C4C}.png',  # first uploaded image
    '/mnt/data/{6D4016D0-79EE-4FFC-B6E3-B6C8984A8788}.png'   # second uploaded image
]

# Copy the images to the imgs folder
for img_file in image_files:
    shutil.copy(img_file, imgs_folder_path)

# Updated HTML content with image links referencing the /docs/imgs folder
updated_html_with_img_folder = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bahyway Portfolio and Blog</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }
        header h1 {
            margin: 0;
        }
        nav ul {
            list-style: none;
            padding: 0;
        }
        nav ul li {
            display: inline;
            margin-right: 20px;
        }
        nav ul li a {
            color: #fff;
            text-decoration: none;
        }
        main {
            padding: 20px;
        }
        .project {
            background-color: #fff;
            margin-bottom: 20px;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }
        .project h2 {
            margin-top: 0;
        }
        .project img {
            max-width: 100%;
            height: auto;
            border-radius: 5px;
        }
        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
            position: absolute;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

<header>
    <h1>Bahyway's Portfolio & Blog</h1>
    <nav>
        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">Portfolio</a></li>
            <li><a href="#">Blog</a></li>
        </ul>
    </nav>
</header>

<main>
    <section class="project">
        <h2>Veterinary Microbial Diseases</h2>
        <img src="imgs/{9B4E157D-C9B4-4866-BF5A-E20AFBCB0C4C}.png" alt="Veterinary Microbial Diseases">
        <p>This project involves a Knowledge Graph visualizing microbial relationships using Dash and LangChain. It demonstrates a deep understanding of the biological domain and machine learning integration.</p>
    </section>

    <section class="project">
        <h2>Building KG with AI</h2>
        <img src="imgs/{6D4016D0-79EE-4FFC-B6E3-B6C8984A8788}.png" alt="Building KG with AI">
        <p>This project involves building a knowledge graph (KG) with AI-driven analytics. We used PyTorch, LangChain, and Graph databases for advanced knowledge representation.</p>
    </section>

    <section class="project">
        <h2>LBP Classification</h2>
        <img src="imgs/{9B4E157D-C9B4-4866-BF5A-E20AFBCB0C4C}.png" alt="LBP Classification">
        <p>Using Local Binary Patterns (LBP) for image classification tasks, this project showcases techniques for real-time data processing and classification using deep learning frameworks.</p>
    </section>
</main>

<footer>
    <p>© 2025 Bahyway. All Rights Reserved.</p>
</footer>

</body>
</html>
"""

# Save the updated HTML with image references pointing to the /docs/imgs folder
final_html_with_img_folder_path = "/mnt/data/portfolio_blog_demo_with_imgs_folder.html"
with open(final_html_with_img_folder_path, "w") as file:
    file.write(updated_html_with_img_folder)

final_html_with_img_folder_path
