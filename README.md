# url-Shortener
# ShortURLs

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Enhanced Interactive Design</title>

    <style>
        :root {
            --primary-color: #4361ee;
            --secondary-color: #3a0ca3;
            --accent-color: #f72585;
            --light-color: #f8f9fa;
            --dark-color: #212529;
            --success-color: #4cc9f0;
            --text-color: #2b2d42;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #e8ecef 0%, #c2e9fb 100%);
            color: var(--text-color);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header */
        header {
            text-align: center;
            margin-bottom: 40px;
            animation: fadeIn 1s ease;
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            color: var(--secondary-color);
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        header p {
            font-size: 1.2rem;
            color: #6c757d;
            max-width: 600px;
            margin: 0 auto;
        }

        /* Centered Section */
        .centered {
            padding: 100px 20px;
            text-align: center;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 15px;
            box-shadow: var(--shadow);
            margin-bottom: 40px;
            transition: var(--transition);
            animation: slideUp 0.8s ease;
        }

        .centered:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
        }

        .centered h2 {
            font-size: 2.2rem;
            margin-bottom: 20px;
            color: var(--primary-color);
        }

        /* Secret Text */
        .secret-text {
            text-align: center;
            font-size: 2rem;
            color: var(--light-color);
            background: linear-gradient(45deg, var(--dark-color), var(--secondary-color));
            padding: 20px;
            border-radius: 10px;
            margin: 30px auto;
            max-width: 600px;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            animation: pulse 2s infinite;
        }

        .secret-text:hover {
            transform: scale(1.03);
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        .secret-text::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(
                to bottom right,
                rgba(255, 255, 255, 0.2),
                rgba(255, 255, 255, 0)
            );
            transform: rotate(45deg);
            transition: var(--transition);
        }

        .secret-text:hover::before {
            animation: shine 1.5s ease;
        }

        /* Buttons */
        .btn_container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 15px;
            margin: 30px 0;
        }

        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: var(--shadow);
        }

        .btn-primary {
            background: var(--primary-color);
            color: white;
        }

        .btn-primary:hover {
            background: var(--secondary-color);
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        .btn-secondary {
            background: var(--accent-color);
            color: white;
        }

        .btn-secondary:hover {
            background: #d81159;
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        .btn-outline {
            background: transparent;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
        }

        .btn-outline:hover {
            background: var(--primary-color);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        /* Table */
        .table-container {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            margin: 40px auto;
            padding: 20px;
            max-width: 95%;
            animation: fadeIn 1s ease;
            transition: var(--transition);
        }

        .table-container:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px auto;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            text-align: left;
        }

        th, td {
            border-bottom: 1px solid #ddd;
            padding: 15px;
            transition: var(--transition);
        }

        th {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            font-weight: 600;
            position: relative;
            cursor: pointer;
        }

        th:hover {
            background: linear-gradient(to right, var(--secondary-color), var(--primary-color));
        }

        th i {
            margin-left: 8px;
            font-size: 0.8rem;
        }

        tr:nth-child(even) {
            background-color: #f8f9fa;
        }

        tr:hover {
            background-color: #e9ecef;
            transform: scale(1.01);
        }

        td:hover {
            background-color: #dee2e6;
        }

        a {
            text-decoration: none;
            color: var(--primary-color);
            font-weight: 500;
            transition: var(--transition);
            position: relative;
        }

        a:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -2px;
            left: 0;
            background-color: var(--primary-color);
            transition: var(--transition);
        }

        a:hover {
            color: var(--secondary-color);
        }

        a:hover:after {
            width: 100%;
            background-color: var(--secondary-color);
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from { 
                opacity: 0;
                transform: translateY(20px);
            }
            to { 
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }

        @keyframes shine {
            0% { transform: translateX(-100%) rotate(45deg); }
            100% { transform: translateX(100%) rotate(45deg); }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .btn_container {
                flex-direction: column;
                align-items: center;
            }
            
            .btn {
                width: 80%;
                justify-content: center;
            }
            
            .centered {
                padding: 60px 20px;
            }
            
            .secret-text {
                font-size: 1.5rem;
                padding: 15px;
            }
            
            table {
                font-size: 0.9rem;
            }
            
            th, td {
                padding: 10px;
            }
        }

        @media (max-width: 480px) {
            header h1 {
                font-size: 2rem;
            }
            
            .centered h2 {
                font-size: 1.8rem;
            }
            
            .secret-text {
                font-size: 1.2rem;
            }
            
            th, td {
                padding: 8px;
            }
        }
    </style>
