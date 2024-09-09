<template>
  <div class="resume">
    <div class="header">
      <img class="profile-pic" src="@/assets/020.jpg" alt="Profile Picture" />
      <div class="info">
        <h1>{{ name }}</h1>
        <div class="contact">
          <p><i class="fas fa-phone"></i> {{ phone }}</p>
          <p><i class="fas fa-envelope"></i> {{ email }}</p>
          <p><i class="fas fa-map-marker-alt"></i> {{ address }}</p>
        </div>
      </div>
    </div>

    <div class="main-content">
      <div class="column left-column">
        <div class="section">
          <h2>EDUCATION</h2>
          <p><strong>{{ education.degree }}</strong></p>
          <p>{{ education.institution }}</p>
          <p>{{ education.period }}</p>
        </div>

        <div class="section">
          <h2>SKILLS</h2>
          <ul>
            <li><strong>Programming languages:</strong> {{ skills.languages.join(', ') }}</li>
            <li><strong>Web Development:</strong> {{ skills.webDevelopment.join(', ') }}</li>
            <li><strong>Database Management:</strong> {{ skills.databaseManagement }}</li>
            <li><strong>Operating Systems:</strong> {{ skills.operatingSystems.join(', ') }}</li>
          </ul>
        </div>

        <div class="section">
          <h2>LANGUAGE</h2>
          <p>{{ language }}</p>
        </div>
      </div>

      <div class="column right-column">
        <div class="section">
          <h2>PROFILE</h2>
          <p>{{ profile }}</p>
        </div>

        <div class="section">
          <h2>EXPERIENCE</h2>
          <div v-for="(job, index) in experience" :key="index">
            <p><strong>{{ job.title }}</strong></p>
            <p>{{ job.description }}</p>
          </div>
        </div>

        <div class="section">
          <h2>INTERESTS</h2>
          <p>{{ interests.join(', ') }}</p>
        </div>

        <div class="section">
          <h2>REFERENCES</h2>
          <p><strong>{{ references.name }}</strong></p>
          <p>{{ references.position }}</p>
          <p>Email: {{ references.email }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Resume',
  data() {
    return {
      profilePic: '@/assets/020.jpg',
      name: 'NAMPHU THANOMRAK',
      phone: '085-567-6400',
      email: 'namphut48@nu.ac.th',
      address: '42/1 moo 8, SriNakhon, Sukhothai',
      education: {
        degree: 'Bachelor of Computer Science',
        institution: 'Naresuan University',
        period: '2021 - Present'
      },
      skills: {
        languages: ['Python', 'Java', 'PHP'],
        webDevelopment: ['HTML', 'CSS', 'Java'],
        databaseManagement: 'MySQL',
        operatingSystems: ['Windows', 'Linux']
      },
      language: 'English (beginner)',
      profile: 'Hello, my name is Namphu Thanomrak, a Computer Science Bachelor\'s degree holder from Naresuan University. I have learned the basics of programming languages: Python, Java, C++, HTML, CSS, JavaScript, and SQL. I aim to develop myself.',
      experience: [
        {
          title: 'Online Bookstore Website Project (Internet Programming Course)',
          description: 'Developed the backend and frontend for an online bookstore, implementing server-side logic using technologies such as PHP, SQL, and Node.js.'
        },
        {
          title: 'Deep Learning for Image Recognition and Detection Application',
          description: 'Participated in a project focused on developing image recognition and detection algorithms using deep learning techniques.'
        }
      ],
      interests: ['Data Analyst', 'Software Engineering', 'Artificial Intelligence'],
      references: {
        name: 'Wuttipong Ruanthong',
        position: 'Naresuan University / Professor',
        email: 'wuttipong@nu.ac.th'
      }
    }
  }
}
</script>

<style scoped>
.resume {
  max-width: 210mm;
  margin: auto;
  padding: 15mm;
  font-family: Arial, sans-serif;
  box-sizing: border-box;
}

/* Header Section */
.header {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
}

.profile-pic {
  width: 120px;
  height: 120px;
  border-radius: 8px;
  margin-right: 15px;
  object-fit: cover;
}

.info {
  flex-grow: 1;
}

.info h1 {
  margin: 0;
  font-size: 2.2em;
  font-weight: bold;
}

.contact p {
  margin: 4px 0;
  font-size: 1.1em;
}

/* Main Content */
.main-content {
  display: flex;
  justify-content: space-between;
  gap: 30px;
}

.column {
  flex: 1;
}

.left-column {
  margin-right: 10px;
}

.right-column {
  margin-left: 10px;
}

.section {
  margin-bottom: 20px;
}

.section h2 {
  font-size: 1.6em;
  font-weight: bold;
  border-bottom: 2px solid #000;
  margin-bottom: 10px;
}

.section p,
.section ul {
  margin: 0;
  font-size: 1em;
}

ul {
  list-style-type: none;
  padding: 0;
}

ul li {
  margin-bottom: 8px;
}

@media (max-width: 576px) {
  .main-content {
    flex-direction: column;
    gap: 0;
  }

  .column {
    width: 100%;
  }

  .header {
    flex-direction: column;
    align-items: flex-start;
  }

  .profile-pic {
    width: 100px;
    height: 100px;
    margin-bottom: 10px;
  }

  .info h1 {
    font-size: 1.8em;
  }

  .contact p {
    font-size: 0.9em;
  }

  .section h2 {
    font-size: 1.4em;
  }

  .section p,
  .section ul {
    font-size: 0.9em;
  }
}

@media (min-width: 576px) {
  .main-content {
    flex-direction: row;
  }
}
</style>
